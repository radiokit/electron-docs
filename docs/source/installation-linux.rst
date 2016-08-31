.. _installation-linux:

Installation on Linux
#####################

Currently the only supported distributions are Ubuntu 14.04 and 16.04 LTS (amd64 architecture).

Installing package
******************

1. Install prerequisities:
   ::

        sudo apt-get install apt-transport-https
        sudo apt-key adv --keyserver pool.sks-keyservers.net --recv-keys 0xD11AA80452796970

2. Add repository:

   a) If you use Ubuntu 14.04 LTS (amd64 architecture)
      ::

            sudo apt-add-repository 'deb [arch=amd64] https://packages.radiokit.org/packages/linux/ubuntu trusty trusty-stable'
            sudo apt-get update

   b) If you use Ubuntu 16.04 LTS (amd64 architecture)
      ::

           sudo apt-add-repository 'deb [arch=amd64] https://packages.radiokit.org/packages/linux/ubuntu xenial stable'
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


Automatic starting & supervision
********************************

If you want to start it with the system, and restart automatically it
in case of failure, please do the following:

1. Create a user for the service:
   ::

        sudo useradd -G audio -m radiokit

2. Create a file named /etc/radiokit/pulse.pa as root:
   ::

        sudo mkdir -p /etc/radiokit/
        sudo nano /etc/radiokit/pulse.pa

   with the following contents:
   ::

        #!/usr/bin/pulseaudio -nF

        .fail

        load-module module-native-protocol-unix auth-group=radiokit auth-cookie-enabled=false srbchannel=true
        load-module module-rescue-streams
        load-module module-always-sink sink_name=null
        load-module module-intended-roles
        load-module module-udev-detect
        set-default-sink null
        set-default-source null.monitor


3. Create a file named /home/radiokit/.pulse/client.conf as root:
   ::

        sudo mkdir -p /home/radiokit/.pulse/
        sudo nano /home/radiokit/.pulse/client.conf

   with the following contents:
   ::

        autospawn=no

  and then change its ownership:
  ::
       sudo chown -R radiokit:radiokit /home/radiokit/.pulse


4. Create a file named /lib/systemd/system/radiokit-pulseaudio.service as root:
   ::

        sudo nano /lib/systemd/system/radiokit-pulseaudio.service

   with the following contents:
   ::

        [Unit]
        Description=RadioKit: PulseAudio

        [Service]
        User=radiokit
        Group=radiokit
        WorkingDirectory=/home/radiokit
        ExecStart=/opt/radiokit-electron-1.2/bin/pulseaudio -F /etc/radiokit/pulse.pa -n
        Environment="LD_LIBRARY_PATH=/opt/radiokit-electron-1.2/lib"
        KillMode=process
        Restart=always
        RestartSec=5s
        TimeoutSec=30s
        LimitNICE=31
        LimitRTPRIO=infinity
        LimitMEMLOCK=infinity
        LimitNOFILE=65535
        LimitNPROC=1024
        LimitCPU=infinity
        IOSchedulingClass=realtime
        IOSchedulingPriority=1

        [Install]
        WantedBy=multi-user.target
        Alias=radiokit-pulseaudio.service

5. Create a file named /lib/systemd/system/radiokit-electron-1.2-daemon.service as root:
   ::

        sudo nano /lib/systemd/system/radiokit-electron-1.2-daemon.service

   with the following contents:
   ::

        [Unit]
        Description=RadioKit Electron 1.2: Daemon
        After=network.target radiokit-pulseaudio.service

        [Service]
        User=radiokit
        Group=radiokit
        WorkingDirectory=/home/radiokit
        ExecStart=/opt/radiokit-electron-1.2/bin/radiokit-electron-daemon-1.2
        Environment="LD_LIBRARY_PATH=/opt/radiokit-electron-1.2/lib"
        KillMode=process
        Restart=always
        RestartSec=5s
        TimeoutSec=30s

        [Install]
        WantedBy=multi-user.target
        Alias=radiokit-electron-1.2.service

6. Reload systemd:
   ::

       sudo systemctl daemon-reload

7. Enable service for PulseAudio sound server:
   ::

       sudo systemctl enable radiokit-pulseaudio.service

8. Enable service for RadioKit Electron itself:
   ::

       sudo systemctl enable radiokit-electron-1.2-daemon.service

9. Start service for PulseAudio sound server:
   ::

       sudo systemctl start radiokit-pulseaudio.service

10. Start service for RadioKit Electron itself:
   ::

       sudo systemctl start radiokit-electron-1.2-daemon.service

From this point service should be started and supervised by the system.

You can check if it is running properly by opening http://localhost:20000.
