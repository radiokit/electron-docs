.. _installation-linux-ubuntu-trusty:

Installation on Ubuntu 14.04
############################

Currently the only supported architecture is 64-bit (amd64).

Installing package
******************

1. Install prerequisities:
   ::

        sudo apt-key adv --keyserver pool.sks-keyservers.net --recv-keys 0xD11AA80452796970

2. Add repository:
   ::

        sudo apt-add-repository 'deb [arch=amd64] http://packages.radiokit.org/packages/linux/ubuntu trusty trusty-stable'
        sudo apt-get update

3. Install package itself:
   ::

        sudo apt-get install radiokit-electron-1.2


Manual starting
***************

If you want to start the daemon for just one time, run the following command
from the terminal:
::

    /opt/radiokit-electron-1.2/bin/radiokit-electron-daemon-1.2

This is however, not recommended as it does not provide supervision.

You can check if it is running properly by opening http://localhost:20000.
