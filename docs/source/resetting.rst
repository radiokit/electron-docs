Resetting configuration
=======================

If you want to reset configuration of existing device, you have to do the
following, according to operating system you use using the following instructions.

Please note that the application after this process will recognize that it is
run at the same device. If you want to totally reset the device, you have
to also remove it from the Patchbay in the web console.

Windows
-------

* Log in as user with administrative privileges
* Press **WindowsKey+R** so "Run" window will appear
* Type **services.msc** in the text field and click OK
* In the Service Manager that will pop up, find **RadioKit Electron 1.2**, select
  it and stop the service using stop button in the toolbar.
* Delete file C:\Windows\System32\config\systemprofile\AppData\Local\radiokit-electron\config.json
* In the Service Manager find **RadioKit Electron 1.2**, select
  it and start the service using start button in the toolbar.
* Once you open http://localhost:20000 you should see password prompt exactly
  as it looked like after installing the application for the first time.

Android
-------

On Android, you just have to reinstall the application.


.. toctree::
   :maxdepth: 2
