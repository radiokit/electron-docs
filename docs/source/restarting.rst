Restarting client application
=============================

Generally speaking, RadioKit Electron's client application is supposed to run
as a background system service, at least on platforms that support doing so.

However, you may want to restart the service.

Please follow instructions appropriate to the client device's operating system:

Windows
-------

Attempt to kill process in the task manager will not succeed. You have to use
windows service manager in order to restart the application.

* Log in as a user with administrative privileges
* Press **WindowsKey+R** so "Run" window will appear
* Type **services.msc** in the text field and click OK
* In the Service Manager that will pop up, find **RadioKit Electron 1.2**, select
  it and stop the service using stop button in the toolbar.
* Delete the file `C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\radiokit-electron\\config.json`
* In the Service Manager find **RadioKit Electron 1.2**, select
  it and start the service using restart button located in the toolbar.


.. toctree::
   :maxdepth: 2
