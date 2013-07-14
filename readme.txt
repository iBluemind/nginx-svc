--- NGINX Service ---

This is a Windows service wrapper for the NGINX HTTP and proxy server.
The service wrapper requires .NET 2.0, which should be installed on most modern Windows machines.


--- Install & Uninstall ---

nginxsvc.exe /install [/silent]
nginxsvc.exe /uninstall [/silent]

/silent is optional and instructs the installer not to show a message of success or failure when
installing or uninstalling the service.


--- Configuration ---

You need to edit the nginxsvc.exe.config file and set the path value to where NGINX is installed,
by default this is set as shown below, but may not be the version or location of your NGINX build.

Set gracefulQuit to use "-s quit" instead of "-s stop" when signalling the NGINX processes to stop.
At odd times, NGINX processes do not stop, set forceStop to have the wrapper forcibly kill the
remaining NGINX processes.

<?xml version="1.0"?>
<configuration>
  <appSettings>
    <add key="nginxPath" value="C:\Program Files (x86)\nginx-1.0.9"/>
    <add key="gracefulQuit" value="false"/>
    <add key="forceStop" value="true"/>
  </appSettings>
</configuration>


--- License ---

See the license.txt file for license and warranty details etc.


--- Copyright, Links and other things ---

Web: http://www.lloydkinsella.net/
Github: https://github.com/lkinsella/nginx-svc
Twitter: http://www.twitter.com/lloydkinsella

Copyright (c)2011 Lloyd Kinsella.


