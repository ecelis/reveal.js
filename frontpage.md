# Oracle 12c

## Instalación básica para LexSys

Sistema de Automatización de Procesos para la Administración de Justicia

ernesto@tic.uno



### Programa

1. Requisitos
2. Descarga de Software
3. Preparación del Sistema Operativo
4. Instalación Oracle Database
5. Creación de Esquema y Tablespace



### Requisitos


#### Hardware

* 2 GB RAM
* SWAP >= RAM
* 6.5 GB Disco Duro
* 50 GB x 3 meses datos


#### Software

* Oracle Linux 5, 6 y 7
* Red Hat Enterprise Linux 5, 6 y 7
* CentOS 5, 6 y 7


#### Descarga de Software

http://www.oracle.com/technetwork/database/enterprise-edition/downloads/



### Preparación del Sistema Operativo

1. Dependencias
2. Descarga de Software
3. Ajuste de Parámetros
4. Directorios y usario oracle


#### Dependencias

    curl -o ora_bootstrap.sh https://descarga.lexsys.net/ora_bootstrap.sh
    chmod +x ora_bootstrap.sh
    ./ora_bootstrap.sh


#### Ajuste de parámetros

/etc/

    kernel /vmlinuz-2.6.32-300.25.1.el6uek.x86_64 ro root=LABEL=/ transparent_hugepage=never


##### Parámetros del Kernel

/etc/sysctl.conf

    fs.aio-max-nr = 1048576
    fs.file-max = 6815744
    kernel.shmall = 2097152
    kernel.shmmax = 536870912
    kernel.shmmni = 4096
    kernel.sem = 250 32000 100 128
    net.ipv4.ip_local_port_range = 9000 65500
    net.core.rmem_default = 262144
    net.core.rmem_max = 4194304
    net.core.wmem_default = 262144
    net.core.wmem_max = 1048576


##### Límite de Recursos del Sistema Operativo

/etc/security/limits.conf

    nofile  soft  1024
    nofile  hard  65536
    nproc   soft  2047
    nproc   hard  16384
    stack   soft  10240
    stack   hard  32768
#### Directorios y usario oracle

    groupadd -g 54321 oinstall
    groupadd -g 54322 dba
    groupadd -g 54323 oper
    groupadd -g 54325 dgdba
    groupadd -g 54327 asmdba
    groupadd -g 54328 asmoper
    groupadd -g 54329 asmadmin
    useradd -u 54321 -g oinstall \  
        -G dba,oper,asmdba,dgdba,asmoper,asmadmin oracle
    passwd oracle
    mkdir -p /u01/app/oracle
    chown -R oracle:oinstall /u01/app
    chmod -R 775 /u01/app


#### Variables de Entorno

    ORACLE_BASE=/u01/app/oracle
    ORACLE_HOME=/u01/app/oracle/product/12.1.0/dbhome_1
    ORACLE_SID=SIGIPPEM_USR



### Instalación Oracle Database



### Esquema y Tablespace



### Referencias

* https://docs.oracle.com/en/database/

