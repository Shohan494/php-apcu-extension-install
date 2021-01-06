# php-apcu-extension-install

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

The end!
Now you should be ready to start developing faster applications! I hope this helped everyone out there who did not find a tutorial on how to install APCu for windows. I also encourage you to leave me some feedback!
