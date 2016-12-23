Resetting configuration
=======================

If you want to reset configuration of existing device, please do the following
steps. That may help if you think that

Please note that the application after this process will recognize that it is
running at the same device. If you want to totally remove the device configuration,
not only local one, but also one stored in the cloud, you have to also remove it
from the Patchbay in the web console.

Windows
-------

* Log in as a user with administrative privileges
* Press **WindowsKey+R** so "Run" window will appear
* Type **services.msc** in the text field and click OK
* In the Service Manager that will pop up, find **RadioKit Electron 1.2**, select
  it and stop the service using stop button located in the toolbar.
* Delete the file `C:\\Windows\\System32\\config\\systemprofile\\AppData\\Local\\radiokit-electron\\config.json`
* In the Service Manager find **RadioKit Electron 1.2**, select
  it and start the service using start button located in the toolbar.
* Once you open http://localhost:20000 you should see password prompt exactly
  as it looked like after installing the application for the first time.

.. toctree::
   :maxdepth: 2
