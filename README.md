### apexi-tutorial


**Disclaimer #1:** Tuning programmable ECUs is extremely difficult and highly advanced. You should not even attempt to do this unless you have a solid understanding of how a fuel injection system works, the effect of ignition timing, etc.  
  
**Disclaimer #2:** A Power FC is not a bolt-on power adder. It's not like adding an intake, where you spend an hour installing it, go to the dyno and gain ten who. With a Power FC, you're likely to _lose power_ or, way worse, blow your engine if you have a poor map in the car. The Power FC has no safety feedback features like the stock ECU. It does what you tell it to do, even if that causes damage to the engine.  
  
**Disclaimer #3:** I do not provide "base maps" or personalized "tune my car over the internet" sessions. Please don't ask me. I have put a great deal of time and effort into making this sticky as easy to understand as possible, but I intend for people to take the ball and run with it after they're done reading it. If you have a _specific_ question about something I've said here and need clarification, please post it in this thread rather than sending me a PM. "Help, my car is knocking" is not a specific question. I'm more than happy to give guidance, but I have to leave the work up to you.  
  
The scope of this sticky is to explain how to install a Power FC and tune it for maximum power. It is here to show you how to become proficient with the FC Edit software included with the FC Datalogit. Advanced tuning topics will be covered by other stickies. To take advantage of the material in this thread, you will _need_ the following three pieces of equipment:  
  
**A'PEXi Power FC  
FC Datalogit (includes FC Edit software)  
wideband oxygen sensor  
laptop computer**  
  
The subject of wideband oxygen sensors has been covered in this sticky:  
  
[Everything you need to know about wideband O2 sensors](http://www.newcelica.org/forums/showthread.php?t=188457)  
  
Also, the Power FC is only compatible with 2000-02 cars. Drive By Wire (DBW) throttle was introduced in 2003 cars, and the Power FC is incompatible with this. You can convert a DBW Celica to a cable throttle, which has been successfully done. The methods described in the following thread are what was used. The thread relating to this can be found here:  
  
[How-to: DBW to cable throttle conversion](http://www.newcelica.org/forums/showthread.php?t=205309)  
  
Another method for solving the DBW issue is running a PFC parallel to the stock ECU. That information can be found here:  
  
[Need a test subject for an 03+ DBW 2ZZ PowerFC install](http://www.newcelica.org/forums/showthread.php?t=224049)  
  
**Where do I purchase a Power FC and FC Datalogit?**  
  
Many places offer Power FC for a reasonable price. That topic is outside the scope of this sticky. The FC Datalogit, however, is much harder to come by. You might have months of the backorder, so plan and be patient. These can be purchased directly from [FC Datalogit](http://www.fc-datalogit.co.nz/) or for a lower price from [Monkeywrench Racing](http://www.monkeywrenchracing.com/). If the Datalogit is backordered at Monkeywrench, it is often faster to get it from FC Datalogit direct.  
  
**Should I get the serial or USB Datalogit?**  
  
The serial model is cheaper, but many newer laptops do not have a serial port. In this case, get the USB version. If you have a serial version and your laptop does not have a serial port, you can buy the Sewell USB adapter from their website:  
  
[Sewell InstaCOM USB to Serial Adapter](http://sewelldirect.com/usbtoserial.asp)  
  
This is the adapter that comes with the USB version of the Datalogit. I have used it successfully, while other adapters like the Belkin have caused FC Edit to lock up during logging, and some, like those found on eBay, often don't even connect to the Datalogit.  
  
**How do I install the Power FC and FC Datalogit?**  
  
The Power FC is a direct replacement for the factory ECU. Take the cover off the ECU (the one that says to never remove it), unplug the harness plugs, and remove the two bolts holding it down (with a 10mm socket). For safety, you should always do this with the negative battery terminal disconnected. The ECU is held in further with two tabs on the side. To release these, stick a flat-head screwdriver down the side of the ECU and remove the tabs. The Power FC will slide right into the spot vacated by the ECU but does not have hold-down bills and is narrower than the factory ECU. Before installing the Power FC, notice the PS2 port on its side. This is where the Datalogit plugs in. With the Power FC installed, you will need to either keep the ECU cover off or drill a hole somewhere in the ECU box to run the Datalogit wire in. Most people drill a hole in the back of the ECU box and run the wire in there, but remember that the battery is right there, so make sure the wire and mortar don't interfere. If you wish to permanently install the Datalogit, you will need to find a way to run the wire from the passenger compartment to the engine bay. I ran mine through the grommet for the steering rack. My Datalogit is mounted above my feet, and the interface cord to the laptop runs into the glove box and is coiled up there. I need to open the glove box to access the cable when tuning.  
  
**Now that everything is hooked up, how do I use FC Edit?**  
  
1\. The first step is to have the car at least in the on position, with or without the engine running. This powers up the Power FC. Start the program FC Edit, which will bring you to the opening screen.  
  
![fcedit-welcome](https://github.com/user-attachments/assets/afd0701e-72fe-4685-a611-349dc4020685)

  
  
You may get a COM port error when starting FC Edit, which means either you have the car off or the COM port is set wrong in FC Edit. Most serial ports will run on COM 1, but the USB will run something else. Go to Setup -> Port in FC Edit to select the correct COM port.  
  
2\. At this point, FC Edit will automatically open the default.dat file in the same folder as the executable file. Take a look at the Settings 1 tab. The default.dat file for the 2ZZ looks like this:  
  

![fcedit-default](https://github.com/user-attachments/assets/62c9e3e2-d884-4761-9fea-22d12ab0fe2b)

  
  
You can change the default file to whatever you wish, but the fact that the default file is so different from any normal map can be helpful.  
  
3\. At this point, you should initialize the Power FC. This function is accessed from the Tools menu at the top of the screen. Initializing the Power FC will erase any previous maps that may have been loaded but, more importantly, will erase any learning of idle settings. This is critical to properly get your car to idle once you're up and running. Let me restate that this will erase any maps loaded in the Power FC and revert to the default map. If you have a map in the Power FC that you intend to use, first save this map to your computer, then initialize the Power FC, then reload your map.  
  
4\. Still, from the Settings 1 tab, click Read All. This will read in all the current data on your Power FC. You will notice the values change on your Settings 1 screen. That is why it's nice to keep the default file as is: because you can visually see that the Read All function has been successful.  
  
5\. If your Power FC still has the default.dat file in it, or you wish to load a different map, do it at this point. You go to File -> Open and select your desired .dat file. If you send or receive Power FC maps through e-mail, it is always a good idea to zip the file first. The .dat files can become corrupted by e-mail systems and become unusable. Now that you have opened your desired map click Write All to write it to the Power FC. Once you've done that, cycle your key off and back on, and do File -> Default in FC Edit. Now do a Read All and see if the values in FC Edit change. This step double-checks that the write function was successful.  
  
6\. Now, you need to let your Power FC learn the idle of your car. There is a 30-minute learn-to-process the Power FC goes through for this. For the best sluggish results, allow this entire 30-minute process to complete. This process should be started with the car cold, although you should not do this on a freezing day so that the car can heat to operating temperature reasonably quickly. There are three phases in the 30-minute learning cycle:  
  

*   For the first 10 minutes, let the car idle with only an average load. You can have the stereo running during this point, as that would be considered a moderate load on the engine.
*   For the second 10 minutes, add in the blower fan.
*   For the third 10 minutes, add in the air conditioning.

  
**Now that everything is installed, FC Edit is running, and my map is loaded, what is all this other stuff?**  
  
FC Edit has ten tabs at the top of the screen and several menus. I will go through them one by one and explain what they do.  
  
**File Menu**  
  
There are five functions under the File menu: Default, Open, Save As, Compare and Exit.  
  

*   Default is basically like Open, only that it opens the default.dat file automatically. This will not work unless you have the default.dat file in the same folder as FC Edit.
*   Open is used for opening saved maps.
*   Save As is used to save your map to a .dat file.
*   Compare is used to compare two maps. It works like a second Open and will open a second map over whatever current map you have open. Any differences between the two maps will be highlighted in yellow or red, depending on positive (red) or negative (yellow) differences. Mousing over a highlighted cell will show you the value in the first map you had open.
*   Exit is used for exiting FC Edit if you didn't know that, back away from your computer and take up another hobby.

  
**Log Menu**  
  
There are three functions under the Log menu: Start, End and Save As. You will notice that all three show corresponding function key shortcuts. These are particularly useful for logging data while driving.  
  

*   Start begins a data logging session.
*   End closes a data logging session.
*   Save As saves your log file. This is not the same as the Save As under the file menu.

  
**Window Menu**  
  
There are eight functions under the Window menu: Monitor, Graph, Chart, Map Watch, Add Watch, Hide Watches, Load Watches and Save Watches.  
  

*   Monitor opens up the Monitor window. From here, you can watch engine telemetry in real-time. You also use Monitor to set up the parameters that will be logged. You can also start, end and save data logging sessions from this window.
*   Graph will show three-dimensional graphs of all your maps.
*   Chart will show your logged data in horizontal chart form.
*   Map Watch will show your logged data on a 20x20 table. Logged values will appear in the cell where they were logged in.
*   Add Watch lets you put real-time parameters displays on the screen, like a digital gauge. This is particularly useful if you have a wideband without a gauge display, such as an Innovative LC-1.
*   Hide Watches removes the watch displays from the screen.
*   Load Watches allows you to load pre-selected watches. Otherwise, you would have to add each look individually every time you open FC Edit.
*   Save Watches saves your current watches, so you can quickly reload them in the future.

  
**Tools Menu**  
  
There are two functions under the Tools menu: Initialize Power FC and ReCalc Base.  
  

*   Initialize Power FC will reset the ECU. This will erase any loaded maps and learned idle settings.
*   ReCalc Base is used to write changes from the INJ map to the Base Map and then reset INJ to all 1.000. This can be useful while tuning to make percentage changes in fueling the map quickly and easily.

  
**Setup Menu**  
  
Four functions are under the Setup menu: Port, Auxilary, Version and Maps.  
  

*   Port is used to select which COM port your computer will use to communicate with the Datalogit.
*   Auxiliary is used to set up the auxiliary ports on the Datalogit, such as the wideband sensor.
*   Version selects between 1ZZ-FE and 2ZZ-GE.
*   Maps is used to select various functions that can be accessed in other ways from other windows.
