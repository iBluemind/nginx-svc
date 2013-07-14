NGINX +PHP service for Windows
==============================

This service for Windows is wrapper for the Nginx server.
The service is created by Lloyd Kinsella, and modifed by Han Manjong, for supporting PHP.

The service wrapper requires .NET 2.0, which should be installed on most modern Windows machines.

Install & Uninstall
===============

nginxsvc.exe /install [/silent]
nginxsvc.exe /uninstall [/silent]

/silent is optional and instructs the installer not to show a message of success or failure when
installing or uninstalling the service.

Configuration
============

You need to edit the nginxsvc.exe.config file and set the path value to where NGINX is installed,
by default this is set as shown below, but may not be the version or location of your NGINX build.

Set gracefulQuit to use "-s quit" instead of "-s stop" when signalling the NGINX processes to stop.
At odd times, NGINX processes do not stop, set forceStop to have the wrapper forcibly kill the
remaining NGINX processes.

<?xml version="1.0"?>
<configuration>
  <appSettings>
    <add key="nginxPath" value="C:\Program Files (x86)\Nginx\1.5.2"/>
    <add key="gracefulQuit" value="false"/>
    <add key="forceStop" value="true"/>
	<add key="php_cgi_path" value="C:\Program Files (x86)\PHP\5.2.17"/>
	<add key="fastcgi_pass" value="127.0.0.1:9000"/>
	<add key="php_ini_path" value="C:\Program Files (x86)\PHP\5.2.17"/>
  </appSettings>
</configuration>

Added functions are php_cgi_path, fastcgi_pass, and php_ini_path.
Set the value of php_cgi_path to where php-cgi.exe is.
And set the php_ini_path to where php.ini is.

License
=======

See the license.txt file for license and warranty details etc.


Credit
=====

Originally developed by Lloyd Kinsella.
Web: http://www.lloydkinsella.net/
Github: https://github.com/lkinsella/nginx-svc
Twitter: http://www.twitter.com/lloydkinsella




