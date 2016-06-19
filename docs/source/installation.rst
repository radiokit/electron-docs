Installation
============

Download the Electron client
-------------------------------

For **Android** phones download the client `here <https://play.google.com/store/apps/details?id=org.radiokit.electron>`_.

For **Windows 32-bit** downlaod the client `here <https://packages.radiokit.org/packages/windows/radiokit-electron/stable/latest-32bit>`_.

For **Windows 64-bit** download the client `here <https://packages.radiokit.org/packages/windows/radiokit-electron/stable/latest-64bit>`_.


Connect your device to console
---------------------------------
Patchbay
-------------

Patchbay is the place where you can connect and manage all your devices that have Electron client installed on them. To access it follow the next steps: 
1. Open the RadioKit console. 
2. Click on the **Electron** box. 
3. Then click on the **Patchbay** tab. 
Here you can se the list of all your accounts. If you have mulitple accounts, select the one you 
want to connect your device with. If you have only one account, the system will redirect you to the Patchbay of your account on its own. 

If you are entering the Patchbay for the first time you will only see white empty board. All your devices with Electron client will be shown here after you add them to the Patchbay. Note that in order for 
devices with Electron client to be able to communicate with each other you have to add each one of them into the Patchbay. A single device with Electron client (example: Androind phone) can not communicate with the system if the 
system (example: your streaming computer) does not have the Electron installed on it as well. 

Add a new device in Patchbay
---------------------------------

In order to connect your device to the system you have to first add it to the Patchbay. In the Patchbay screen, you will see three buttons
in the upper left corner. The buttons are: Add device, Edit device and Delete (garbage bin icon).  

1. Click on the **Add device** button. A pop-up screen will come up asking you to name your new device. 
2. Insert the name of your new device (example: Journalist one) and click the Add device button. 
Another pop-up screen will come up containg the set up code for your new device as well as the download links to Electron clients. 

**Bear in mind that each code is valid for only 15 minutes after which you will have to start the set up again if you need a new working code**

3. Copy or write down your code and click Close button. Your device will now appear on the Patchbay board. It will look like a blue rectangle and it will have the name 
you gave it, but **it won't be active until you put the code in the Electron client**. 

Insert the Patchbay code in the Electron client
----------------------------------------------------

Open your Electron client on your Android phone or on your Windows system. The welcome screen will ask you to insert the code you have just recived in the previous step. 
Insert the code and click the **Sign in** button. Your client is now active in the Patchbay. Your client will now show you the screen with 2 options, to capture
or playback the sound. However it will still not be able to transmit audio until you complete the next step. 

Connecting your devices in Patchbay
----------------------------------------

After you have completed the previous step and instered the code in you device go back to the Patchbay in the RadioKit console. Your device in the Patchbay (blue rectangle)
will now show all of it's audio interfaces (inputs and outputs) in the form of white squares. The number of squares will vary depending on how many audio inputs/outputs your device has.
By clicking one of the interfaces of your device, it's square will change the color to yellow and allow you to connect it to another device in your Patchbay. Choose the input/output on the second device
and click that square. Now you should be able to see a black line connecting these two interfaces (squares). Voila! Your devices are now connected and ready to communicate.  

Editing names of devices in Patchbay
-----------------------------------------

If you want to edit the name of one of your devices from Patchbay, simply click on it (it will become red) and click the **Edit device** button in the upper left 
corner of Patchbay screen.

Disconnecting devices in Patchbay
--------------------------------------

If you want to disconnect the communication link between your devices in Patchbay, simply click on it (the balck line) and click the delete button in the upper left 
corner of Patchbay screen (garbage bin icon).  

Deleting devices in Patchbay
---------------------------------

If you want to remove one of your devices from Patchbay, simply click on it (it will become red) and click the delete button in the upper left 
corner of Patchbay screen (garbage bin icon).  


.. toctree::
   :maxdepth: 2
