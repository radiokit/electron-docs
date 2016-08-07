Supported software and hardware
===============================

Operating systems
-----------------

RadioKit Electron client app is supported on:

* Windows 7 or newer (both 32 and 64-bit)
* Android 4.1 or newer (ARM, ARMv7, ARM64, x86 and x86_64 processors)

It is technically prepared to work, however not released yet for:

* Ubuntu 16.04 LTS (amd64)
* Raspbian Jessie (armhf)
* Mac OS X (Intel 64-bit)
* iOS


Virtual Sound Cards
-------------------

We have been testing and sucessfully using RadioKit Electron client app with
the following virtual sound cards:

* AXIA IP-Driver for Windows,
* VoiceMeeter for Windows

Hardware
--------

Windows
```````

On Windows any sound card that supports Direct Sound drivers (which mean
virtually any sound card) should work.

We are relying on DirectSound instead of chasing the newest drivers such as
WASAPI to provide maximum backwards compatibility. Windows 7 are still not
uncommon in may radio stations and we need to ensure that these users can use
RadioKit Electron. Even if we add support for WASAPI, ASIO at some point,
we will provide backwards compatibility for DirectSound.

Sound cards that are known to work:

* ESI Juli@

Sound cards that are known to cause issues in the current version:

* Tascam US 2x2

Of course we support any soundcard that is detected as Generic Audio Device
and built-in soundcards.

Android
```````

On Android we are limited to boundaries of the device and particular operating
system build of the device vendor.

It does not limit support for microphone plugged into mic/headphone socket. But
that means that newer and more decent phones will support USB sound cards
(but only these that are detected as Generic Audio Device and have quite low
power consumption), but some will refuse to do so, despite having recent
version of the Android OS.

Sound cards/phones known to work:

* LG Nexus 4 + Android 5.0 + Behringer UCA202

Notes
-----

We will do our best to expand the list of devices known to work.

We encourage our users to share their experiences. Please send us an e-mail
to info@radiokit.org if you want to contribute.
