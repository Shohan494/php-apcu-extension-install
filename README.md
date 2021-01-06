# php-apcu-extension-install

## Windows

 Install APCu on Windows
Assumptions
-I assume that you know what is APC - Alternative PHP cache 
-You want to install APCu because APC is not compatible anymore with PHP 5.5.x
-You want to install APCu for wamp, xampp. Mostly windows web development platforms for PHP

Instructions
Pre: All directory locations might be different for you depending on your wamp installation folder and your PHP/apache versions.

1. Go to http://pecl.php.net/package/APCu, there is a table with available releases
2.Choose whatever release suits you better(I chose 4.0.5 DLL)  
3. Choose package from DLL list, depending on what Windows you are using(32 bits/64 bits) and PHP version. In my case I chose 5.5 Thread Safe (TS) x86
4. Unzip the archive, copy php_apcu.dll in C:\wamp\bin\php\php5.5.12\ext.
5. Go to C:\wamp\bin\apache\apache2.4.9\bin open php.ini  and add the following lines(I just added them at the end of the file):
[apcu]
extension="C:\wamp\bin\php\php5.5.12\ext\php_apcu.dll"
apc.enabled=1
apc.shm_size=32M
apc.ttl=7200
apc.enable_cli=1
apc.serializer=php

This are recommended configurations located in INSTALL file from the php_apcu archive, excepting the location of the DLL file.

6. Restart wamp
7. Go to http://localhost/phpinfo.php and check if apcu configuration table appears and apcu is enabled
8. If you also want to use apcu for PHP CLI then you only need to add in C:\wamp\bin\php\php5.5.12\bin\php.ini the config lines you added at step 5 in apache's php.ini.

## Linux

Known issues

There are few known issues, some partially related to the project itself (to be solved at some point).
Php xml extension#
note

This might happen when trying to install packages from composer

    Follow this guide
        or simply call this commands:
            sudo apt-get install php-xml
            sudo service apache2 restart

Php Apcu extension#
note

This might happen when trying to rebuild the cache via ache:clear and cache:warmup

    Call this commands:

    sudo apt install php-apcu,
    sudo nano /etc/php/7.4/mods-available/apcu.ini

Now this should be the content of the apcu.ini, and if it's not then add it to the file:
```
extension=apcu.so
apc.enabled=1
apc.write_lock=1
apc.shm_size=100M
apc.slam_defense=0apc.enable_cli=1

    now call sudo service apache2 restart
```
