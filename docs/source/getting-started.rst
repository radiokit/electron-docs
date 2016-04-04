Getting Started
===============

RadioKit Electron takes different approach than most Audio Over IP systems
present on the market. It was designed with focus on easing both journalists'
and sound engineers' lives, so there's a clear distinction between roles of
*user* (who is usually a journalist but it may also mean sound device attached
to the network) of the system and its *administrator*.

The idea is to keep functionality of users as minimum as it is necessary to
operate and provide engineers centralized, web-based control panel so they can
supervise and control behaviour of all connected devices from one place.

Device Pool
^^^^^^^^^^^

In this documentation we will refer to the *client* when talking about device that
is connected to the network and is capable of playing or capturing audio.

All these devices form your Device Pool, and you can route sound between their
audio interfaces. If they contain more than one audio interface, each is treated
separately. One client can do multiple transmissions in parallel.

Workflow
^^^^^^^^

The workflow essentially looks like the following:

* Administrator installs client application on all devices (clients) that are
  supposed to route the sound over the internet.
* Administrator adds all clients to the Device Pool in the web-based Console
  (control panel). For each device system generates unique one-off key that
  is valid for 15 minutes.
* User or administrator types appropriate one-off key in all clients, they
  synchronize with the system.
* Administrator configures desired routing between clients' audio interfaces.
* Administrator remotely turns on or off transmission from/to individual
  audio interfaces when necessary.


.. toctree::
   :maxdepth: 2
