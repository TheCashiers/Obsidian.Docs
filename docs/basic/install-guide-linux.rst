Installation Guide on Linux
===========================

This document is a guide for installation Obsidian on a Linux Distribution. For installation on Windows, see :doc:`install-guide-windows`

Obtain Compiled Obsidian Files
------------------------------

Compile by configuration bash script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You need to compile Obsidian on your own because we have not provided compiled files. A bash script has been provided for configuring compiling environment.

You can configure compiling environment by the following command if in Ubuntu::

    curl -o- https://raw.githubusercontent.com/ZA-PT/Obsidian/canary/configure_env/ubuntu/configure_env.sh | bash

After configuration, you can build and publish Obsidian::

    ./build.sh | dotnet publish

All runnable files can be found in /home/Obsidian/src/Debug/netcoreapp2.0/publish

Remember to obtain root permissions before you run.

Run Obsidian
------------

Change your working directory of your shell to published Obsidian files,  /home/Obsidian/src/Debug/netcoreapp2.0/publish in default.
Run Obsidian by the following command::

    dotnet Obsidian.dll

Obsidian will host itself and listen on port 5000 in default. You can visit http://localhost:5000/ to access Obsidian.

Configure Reverse Proxy Server
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
You need to configure a reverse proxy server if you want to host more websites on your server and access through port 80. A reverse proxy server is able to transfer HTTP requests between Web Server and Obsidian.

In this sector, we use Nginx as web server and configure a reverse proxy server on it.

Install Nginx, add a new vhost with the following configuration::

    server {
        listen 80;
        server_name yourdomain;
        location / {
            proxy_pass http://localhost:5000;
            proxy_http_version 1.1;
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection keep-alive;
            proxy_set_header Host $http_host;
            proxy_cache_bypass $http_upgrade;
        }
    }

save and restart Nginx, now you can visit Obsidian through yourdomain.

Install Obsidian as Service
^^^^^^^^^^^^^^^^^^^^^^^^^^^
In order to make Obsidian start automatically, Obsidian must be installed as service or run by other monitoring software. In this sector, we use Supervisor as monitoring software, which can monitor Obsidian and restart it automatically.

Install Supervisor, add a new program with the following configuration::

    [program:obsidian]
    directory = /home/Obsidian/src/Debug/netcoreapp2.0/publish
    command = dotnet Obsidian.dll
    autostart = true     
    startsecs = 5        
    autorestart = true   
    startretries = 3     
    user = www
    redirect_stderr = true  
    stdout_logfile_maxbytes = 20MB  
    stdout_logfile_backups = 20     
    stdout_logfile = /data/logs/Obsidian_stdout.log


Please make sure that every part of path exists, or it can not run correctly. Save this configuration files in Supervisor Configuration Directory.

Finally, refresh Supervisor::

    supervisorctl update

Obsidian will automatically run now.

Install MongoDB
^^^^^^^^^^^^^^^

Obsidian stores its datas in MongoDB so you need to install Mongodb. If your MongoDB listen at default port, Obsidian will work correctly.

If you want to set a custom MongoDB connection string, edit appsettings.json in Obsidian working directory, /home/Obsidian/src/Debug/netcoreapp2.0/publish/appsettings.json default::

    {
        "ApplicationInsights": {
            "InstrumentationKey": ""
        },
        "Logging": {
            "IncludeScopes": false,
            "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
            }
        },
        "OAuth20": {
            "TokenAudience": "ObsidianAud",
            "TokenIssuer": "Obsidian"
        },
        "ConnectionStrings": {
            "MongoDB": "mongodb://127.0.0.1:27017"
        }
    }

replace "MongoDB" sector will correct connection string.

Configure Obsidian
------------------

Now visit http://yourdomain/firstrun to setup Obsidian. You need to provide administrator's username, password and Obsidian URL.

Please make sure that Obsidian has permissions creating files in its working directory because The FirstRun program will create init.txt after setting up.

Finally, Obsidian will redirect you to Management Portal, where you can create scope,user or client.

Eventually, you have your Obsidian installed.