Installation
############

Windows
*******

Download and install the latest version of the client `here <https://packages.radiokit.org/packages/windows/electron/stable>`_.

Android
*******

Download the client `here <https://play.google.com/store/apps/details?id=org.radiokit.electron>`_.

Linux (Ubuntu 16.04 64-bit)
***************************

1. Add repository with packages:
   ::

        sudo apt-get install apt-transport-https
        sudo apt-add-repository 'deb [arch=amd64] https://packages.radiokit.org/packages/linux/ubuntu xenial stable'
        sudo gpg --keyserver hkp://pool.sks-keyservers.net --recv-keys 0xD11AA80452796970
        sudo apt-get update

2. Install package itself:
   ::

        sudo apt-get install radiokit-electron-1.2

   At this point the application is installed. If you want to start the daemon for
   just one time, run the following command from the terminal:
   ::

        /opt/radiokit-electron-1.2/bin/radiokit-electron-daemon-1.2

   If you want to start it with the system, and restart automatically in case
   of failure, please do the following:

1. Create a user for the service: sudo useradd -m radiokit-electron
2. Create a file named /etc/radiokit/electron/pulse.pa as root:
   ::

        sudo mkdir -p /etc/radiokit/electron/
        sudo nano /etc/radiokit/electron/pulse.pa

   with the following contents:
   ::

        #!/usr/bin/pulseaudio -nF

        .fail

        load-module module-native-protocol-unix auth-group=app auth-cookie-enabled=false srbchannel=true

        ### Automatically move streams to the default sink if the sink they are
        ### connected to dies, similar for sources
        load-module module-rescue-streams

        ### Make sure we always have a sink around, even if it is a null sink.
        load-module module-always-sink sink_name=null

        ### Honour intended role device property
        load-module module-intended-roles

        ### Make some devices default
        set-default-sink null
        set-default-source null.monitor


3. Create a file named /lib/systemd/system/radiokit-electron-1.2-pulseaudio.service as root:
   ::

        sudo nano /lib/systemd/system/radiokit-electron-1.2-pulseaudio.service

   with the following contents:
   ::

        [Unit]
        Description=RadioKit Electron 1.2: PulseAudio

        [Service]
        User=radiokit-electron
        Group=radiokit-electron
        WorkingDirectory=/home/radiokit-electron
        ExecStart=/opt/radiokit-electron-1.2/bin/pulseaudio -F /etc/radiokit/electron/pulse.pa -n
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
        Alias=radiokit-electron-1.2-pulseaudio.service

4. Create a file named /lib/systemd/system/radiokit-electron-1.2-daemon.service as root:
   ::

        sudo nano /lib/systemd/system/radiokit-electron-1.2-daemon.service

with the following contents:
   ::

        [Unit]
        Description=RadioKit Electron 1.2: Daemon
        After=network.target radiokit-electron-1.2-pulseaudio.service

        [Service]
        User=radiokit-electron
        Group=radiokit-electron
        WorkingDirectory=/home/radiokit-electron
        ExecStart=/opt/radiokit-electron-1.2/bin/radiokit-electron-daemon-1.2
        Environment="LD_LIBRARY_PATH=/opt/radiokit-electron-1.2/lib"
        KillMode=process
        Restart=always
        RestartSec=5s
        TimeoutSec=30s

        [Install]
        WantedBy=multi-user.target
        Alias=radiokit-electron-1.2.service

5. Reload systemd: `sudo systemctl daemon-reload`
6. Enable service: `sudo systemctl enable radiokit-electron-1.2-pulseaudio.service`
7. Enable service: `sudo systemctl enable radiokit-electron-1.2-daemon.service`
8. Start service: `sudo systemctl start radiokit-electron-1.2-pulseaudio.service`
9. Start service: `sudo systemctl start radiokit-electron-1.2-daemon.service`


.. toctree   ::
   :maxdepth: 2
