Installation Guide on Linux
===========================

This document is a guide for installation Obsidian on a Linux Distribution. For installation on Windows, see :doc:`install-guide-windows`

Obtain Compiled Obsidian Files
------------------------------

Compile by configuration bash script
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You need to compile Obsidian on your own because we have not provided compiled files. A bash script has been provided for configuring compiling environment.

You can configure compiling environment by the following command if in Ubuntu:

    **curl -o- https://raw.githubusercontent.com/ZA-PT/Obsidian/canary/configure_env/ubuntu/configure_env.sh | bash**

After configuration, you can build and publish Obsidian:

    **./build.sh**

    **dotnet publish**

All runnable files can be found in /home/Obsidian/src/Debug/netcoreapp2.0/publish

Remember to obtain root permissions before your run.

Compile Manually
^^^^^^^^^^^^^^^^
