# 备份及恢复EayunOS管理端

|项目编号||项目名称|备份及恢复EayunOS管理端|测试日期|2015.9.21|测试人员|何稳|
|---|---|---|---|---|---|---|---|
|测试用例编号||测试用例名称|ovirt-engine数据库及配置文件|作者|何稳|||
|测试用例描述(方法和目的)|||在虚拟机上安装ovirt-engine用来对ovirt-engine数据库内容和配置文件进行备份及恢复|||||
|测试环境设置|||在虚拟机上安装ovirt-engine||||||

**测试步骤**
##使用engine-backup程序对数据库及配置文件进行备份

**简要说明**：数据是一定不能丢的，OVIRT开发此脚本程序帮助您实现这一目标。 

engine-backup是将备份和恢复统一到一起的程序，根据用户的参数而做区别。

先来查看engine-backup的使用帮助：

    engine-backup --help
    engine-backup: backup and restore ovirt-engine environment
    USAGE:
      /usr/bin/engine-backup [--mode=MODE] [--scope=SCOPE] [--file=FILE] [--log=FILE]
    MODE is one of the following:
      backup                  backup system into FILE
      restore                 restore system from FILE
    SCOPE is one of the following:
      all                     complete backup/restore (default)
      db                      database only
    --file=FILE                file to use during backup or restore
    --log=FILE                 log file to use
    --change-db-credentials    activate the following options, to restore
                            the database to a different location etc.
                            If used, existing credentials are ignored.
    --db-host=host             set database host
    --db-port=port             set database port
    --db-user=user             set database user
    --db-passfile=file         set database password - read from file
    --db-password=pass         set database password
    --db-password              set database password - interactively
    --db-name=name             set database name
    --db-secured               set a secured connection
    --db-secured-validation    validate host
    
以下是使用全部参数的例子：

    engine-backup --mode=backup --scope=all --file=backup --log=backup.log
    --change-db-credentials --db-host=localhost--db-port=5432 --db-user=engine
    --db-password=ts4OO3muebXoKh2BLSGSwx --db-name=engine
    
以上例子中--db-user和--db-name=engine默认情况下为engine。
--db-password是/etc/ovirt-engine/engine.conf.d/10-setup-database.conf中的数据库密码。

如果以上例子成功执行，会在当前目录下生成一个backup打包文件，最好将此文件放在您的远程备份环境中，以免丢失。

##从备份文件中恢复系统

为了达到测试的目的，在恢复系统之前，首先要将数据库删除，为了预防有的用户正在使用数据库而无法删除数据库这种情况，使用如下命令清空数据库：

`#engine-cleanup`

使用如下命令初始化并删除数据库：

    # service postgresql initdb
    # service postgresql start
    # chkconfig postgresql on
    #su postgres
    $dropdb engine;
    
接下来是恢复数据库

在恢复数据库之前，首先要创建新的数据库，用以存放备份中的数据，使用如下命令进入数据库命令行环境：

`#sudo -u postgres psql`

创建数据库用户例子：

    postgres=# create role [user name] with login encrypted password '[password]';
    #[user name] 默认情况下是engine
    # [password] 是/etc/ovirt-engine/engine.conf.d/10-setup-database.conf中的数据库密码

在数据库命令行环境中输入\q退出数据库命令行环境。
    
在上述例子中如若找不到数据库密码，可以使用如下命令解压backup文件：

`#tar -jxvf backup`

解压完成后会在当前目录下产生一个files文件夹，数据库密码可在files/etc/ovirt-engine/engine.conf.d/10-setup-database.conf中找到。

创建数据库例子：

    sudo -u postgres -O engine engine
    其中第一个engine为数据库用户名，第二个engine为数据库名
    
如果数据库是全新安装的或者之前未曾配置该步骤的的，编辑文件 /var/lib/pgsql/data/pg_hba.conf，并在紧接着以 Local 开头的那一行下面添加如下内容：

    host [database name] [user name] 0.0.0.0/0 md5
    host [database name] [user name] ::0/0 md5
    
最后恢复数据库：

    #service postgresql restart
    #cd [your backup parent directory]
    engine-backup --mode=restore --file=backup --log=backup.log
    --change-db-credentials --db-host=localhost--db-port=5432 --db-user=engine
    --db-password=ts4OO3muebXoKh2BLSGSwx --db-name=engine
    
如若在恢复过程中出现关于files的错误提示，手动删除之前解压产生的files文件夹及文件夹里的所有文件，再次执行恢复命令即可。
至此，数据库恢复成功，再次执行setup-engine即可。

##恢复配置文件

    #tar -jxvf backup
    #cd files
    #mv /etc/pki/ovirt-engine/ /etc/pki/
    #mv /etc/httpd/conf.d/ /etc/httpd/
    #mv /etc/ovirt-engine /etc/
    #service ovirt-engine restart
    #service httpd restart
    
至此，配置文件恢复成功。
    
