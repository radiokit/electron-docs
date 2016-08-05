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
* In the Service Manager find **RadioKit Electron 1.2**, select
  it and start the service using restart button located in the toolbar.

After a while the service should be restarted.

.. toctree::
   :maxdepth: 2
