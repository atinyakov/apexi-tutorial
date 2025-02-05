### apexi-tutorial
Reviewing tutorial from [this](https://www.newcelica.org/threads/how-to-power-fc-and-fc-datalogit-tuning.258454/) page with Wayback machine

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

  **Base Map**  
  
The Base Map is the most important map and so I will explain it first. The Base Map looks like this:  
  
![fcedit-basemap](https://github.com/user-attachments/assets/72618cbe-7edc-4888-a489-a46f7608ff21)


  
  
The Base Map tab is one of four "map" screens. The numerical values across the top of the table represent rpm breakpoints and the values down the left side represent "load" breakpoints. "Load" is a value that represents load on the engine. It is calculated from several measurements, including airflow (from the mass airflow sensor) and throttle position. The way the Power FC actually calculates load is unknown, but in general, idle and cruise situations will have low load while full throttle will have high load.  
  
The values in Base Map are injector on-times in milliseconds. The reason the tab is called Base Map is because these are the raw injection values before and corrections. Much of the rest of what FC Edit does is apply corrections to these values.  
  
**INJ Tab**  
  
INJ stands for Injection. The screen looks like this:  

  
![fcedit-inj](https://github.com/user-attachments/assets/4e2a9c90-8ba0-4c30-a48d-7c403396d0ee)

  
  
The values in INJ are a percentage correction of the fuel injection. A value of 1.000 means 100%, which is no correction. Values above 1.000 will add fuel while values below 1.000 will take it away. Most common Power FC maps you will find on the internet will have this map set to all 1.000. Using the INJ map in this way will cause the O2 Sensor Feedback function to not work properly. That function will be explained later in this tutorial.  
  
There is much debate amongst different tuners as to the "correct" use of the INJ map. Bear in mind that any method will ultimately work, as INJ and Base Map are always multiplied for final tuning. How you use the map is entirely up to personal taste. Many people like to call this map a "target AFR" map, meaning that you set the values to what your desired AFR would be as a ratio (14.7 / desired AFR). This in theory gives you the enrichment you need for things like full throttle. Once the target AFR is set, any subsequent fueling changes would be made on the Base Map and the INJ map would never be touched. It should be pointed out that this method will only work when using FC Edit and won't work with the Commander. On the Commander, you don't have access to the Base Map, so fueling changes are made on the INJ map. The writers of FC Edit added the ReCalc Base function, which writes changes made on the INJ map to the Base Map and then resets INJ to 1.000. The purpose of this is to do percentage based fuel adjustments. If you wanted to add 4% fuel to certain cells in your Base Map, you would type in 1.040 in the corresponding values in the the INJ map. The Power FC can only understand certain values, so FC Edit will round your 1.040 to the closest possible value. At this point, you could leave your corrections on the INJ map, or you could write the changes to your Base Map using ReCalc Base.  
  
Back to the use of INJ as a target AFR table, there are a few problems with using it this way. First is that the target AFR is not always the same in a given cell. This occurs mainly at part throttle. You will find midrange load cells that you will pass through while cruising and accelerating slightly to maintain speed or change lanes. You will want your AFR to remain around stoichiometric (14.7) under these conditions. But you will also find that under part-throttle acceleration, you will pass through the same cells. Under an acceleration condition, you'll want a richer AFR. So essentially, there is no target AFR for certain cells.  
  
The second issue with INJ as a target AFR table is that it is not the only form of possible enrichment. When using these other enrichment conditions, you will actually be doubling your enrichment. However, many people don't use alternate forms of enrichment so this doesn't come into play.  
  
The alternative to using the INJ map as target AFR map is to use it for percentage-based fuel adjustments or leave it all at 1.000, as many common maps have it. As I've gained more experience tuning the Power FC, this is the method I prefer. There are a few reasons for this:  
  
First, it makes it significantly easier to write maps from scratch for custom setups. You simply scale fueling linearly in the Base Map and then use INJ to make adjustments up and down from your ideal fueling. I have found that enrichment is based almost completely on throttle position and so I put my enrichment there, which allows me to leave my Base Map essentially flat. I'll get into that enrichment setting and the advantages of this later in the tutorial.  
  
The second reason is the elimination of the mixed target AFR's at part-throttle. By using throttle position-based enrichment rather than a set target AFR on a table, you're able to get lean while cruising and rich while accelerating using the same cell. Again, this will be explained more fully later.  
  
The final reason is that in practice, I do not use the O2 Feedback Control function, as I find it to work incredibly poorly. So messing up its functionality through "improper" use of the INJ map is not a concern for me.  
  
**IGN Tab**  
  
IGN stands for Ignition. The screen looks like this:  

  
![fcedit-ign](https://github.com/user-attachments/assets/64a380f0-3e85-47fd-b192-fc4f3f07aace)

  
  
The values on the Ignition map are degrees of ignition advance. This means how many degrees before the piston reaches Top Dead Center (TDC) on the compression stroke that the ignition system will fire the spark plug.  
  
**VVT Map**  
  
VVT stands for variable valve timing. The screen will look like this:  
  

![fcedit-vvt](https://github.com/user-attachments/assets/23b3ae5e-c292-4873-98e3-1634d2c5af09)

  
  
Both the 1ZZ and 2ZZ engines have a variable intake camshaft. This is the VVT-i system. The values in the map correspond to advancing or retarding the intake cam. There is no proof of what these values actually represent, but most people feel that 1 on the VVT map roughly equals or exactly equals one degree of movement of the camshaft. The common belief is that a range of 0-55 represents the maximum effective range of the system, with 0 being the most cam advance and 55 being the least. There is also evidence that 50 is the actual minimum cam advance setting. A Toyota technical document explaining fow the VVT-i system works and what settings generally work in different conditions can be found here:  
  
[http://users.ameritech.net/trdcelica/VVT\_Explanation.pdf](http://users.ameritech.net/trdcelica/VVT_Explanation.pdf)  
  
**Settings 1 Tab**  
  
Settings 1 is the first of five tabs of basic settings and correction factors. The screen looks like this:  
  

![fcedit-settings1](https://github.com/user-attachments/assets/bf6550b4-abe8-4aca-ae0a-caebb61b3288)

  
_Boost Control Box_  
\-The FC Datalogit is able to function as a boost controller. This feature is most commonly used on RX-7's and is not used on the Celica. The feature is completely deactivated in the 1ZZ/2ZZ version of the firmware.  
  
_Function Select Box_  
\-There are five functions that can be turned on and off in this box.  
1\. Boost cntrl kit - Boost Control function. Default is off, leave it off.  
2\. Inj/AirF Warn - Flashes a long pulse on the check engine light if you reach 100% duty cycle on the fuel injectors. Default is on, leave it on.  
3\. Knock Warning - Flashes a short pulse on the check engine light if knock goes above a pre-set threshold. Default is on, leave it on.  
4\. O2 F/B Control - Takes feedback from the oxygen sensor and attempts to compensate injection to achieve a 14.7:1 air fuel ratio. Default is on, turn off for tuning and on if you want post-tuning. This function is tricky and making it work is not simple. Many people, myself included, feel that it works so poorly that it is left off permanantly.  
5\. Idle-IG Cntrl - Controls ignition timing at idle to try and maintain target idle rpm. Advances timing when rpm is below target and retards it when above target. The default is on, leave it on.  
  
\*\*There is a bug with either the Power FC or FC Edit that makes O2 F/B Control very difficult to turn off and keep off. I've found the best way to work around this is change the default.dat map to have these off and re-save it. I'm not sure this has any effect but it at least eliminates possibilities. When I switch these functions off, I will hit Update, then cycle the key on and off. Then Read All and see if they come back on.  
  
_Rev / Idle Box_  
\-There are seven parameters in this box:  
1\. Rev Limit - Rev limiter, where fuel cut occurs.  
2\. VTLI High - RPM where lift engages on acceleration.  
3\. VTLI Low - RPM that lift will hold to on deceleration (such as shifting gears).  
4\. F/C A/E - Fuel cut recovery rpm with air conditioning off. When you let off the throttle, the injectors will shut off. This is the rpm where they will turn back on.  
5\. F/C A/C - Fuel cut recovery rpm with air conditioning on.  
6\. Idle A/E - Idle rpm with air conditioning off.  
7\. Idle A/C - Idle rpm with air conditioning on.  
  
_Knock Warn Box_  
\-Knock warn has two parameters: Thresh and Setting.  
  
1\. Thresh means threshold, and means the maximum knock value that will be tolerated before the check engine light will flash as a warning. It should be noted that 2000-01 cars have a different knock sensor than 2002 and later cars and will typically have higher knock values. The value of the threshold in the default 2ZZ map is 60, which is unrealistically high. The only way to properly set this value is to make a calibration curve for your knock sensor. That topic is covered in this thread:  
  
[http://www.newcelica.org/forums/showthread.php?t=247596](http://www.newcelica.org/forums/showthread.php?t=247596)  
  
One other thing to note is that very hard shifts (typically when racing) will cause very high spikes in knock sensor activity. Do not confuse this as real knock.  
  
2\. Setting - Flash time in milliseconds for the warning. No reason to change this.  
  
_O2 Feedback Box_  
\-The setting here relates to the INJ map. Any cell with an INJ value below the setting value will be subject to O2 feedback/correction provided the function is turned on. Before I showed how most people use the INJ map, for fuel adjustments, and then ReCelc Base and set all the values back to 1.000. As you can see, this will make every cell in the map subject of O2 Feedback Control if the function is on and the default setting value is used. You need to pick the setting value so that you are only applying O2 feedback correction to cells very near stoichiometric. I use a value of 1.035, which corresponds to a commanded AFR of 14.2:1 (assuming 14.7:1 as base AFR value). This would work well when using the INJ map as a target AFR table. However, in practice this function works extremely poorly. It is very slow to respond and wildly overshoots stoichiometric. I find that at idle, the car will fluctuate between 12.5 and 16.5 AFR with this setting turned on. Unfortunately, the settings that control the response of this function are protected and hidden on the Power FC. On more advanced ECU's such as the AEM EMS, these functions are tunable. Since the function essentially doesn't work, I just leave it off permanently. With the function off, you no longer have a real consideration with how you use your INJ map.  
  
_Protect Box_  
\-This box would be used by tuners to make certain settings inaccessible with a Power FC Commander. Since you are using FC Edit, obviously this doesn't apply. Just uncheck everything here.  
  
_Version Box_  
\- This will show the Program String (2ZZ-GE in my case) and the Program Version. 99% of the time, this will be 2.71A for a 2ZZ engine, but I have come across a Power FC from and XS turbo kit that had vertion T2.71. If the v1.120 will not work for this version, a version v1.110c does exist that will.  
  
**Settings 2 Tab**  
  
Settings 2 is the tab where most of the main correction factors are. It looks like this:  
  

![fcedit-settings2](https://github.com/user-attachments/assets/07daa3ba-5899-4f9d-8445-4d333459b1d5)

  
  
There are eight boxes for various correction factors, explained below.  
  
_Water Temp Correction_  
\-There are two columns for water temp correction. The one on the left is for "light load" and the one on the right is for "heavy load". If you look at the default values, you will see more enrichment at high load and cold temperatures. You will find that the default values are absurd, and need to be reduced significantly for proper fuel mixture.  
  
_Accelerate Injector (mS)_  
  
\-These settings increase injector duration when you accelerate suddenly. This is done to prevent knock when the throttle is quickly pressed. There are three values: RPM, Amount and Decay. RPM is simply a breakpoint, Amount is the increase in injector duration and decay is the amount of time the enrichment lasts. A wideband oxygen sensor is needed to properly adjust these. To adjust this, bring your car at steady throttle to one of the breakpoints (example: 3000 rpm) and then suddenly increase the throttle. Watch the value on the wideband. Increase or decrease the value of Amount until you hit the desired AFR on acceleration. Typically, if you have rich/lean issues, it has to do with your map, not this setting.  
  
_Cranking (mS)_  
\-These are injector duration settings at various water temperatures. The default settings are too long, and the Monkeywrench settings are even worse, especially at high temperatures. If you are getting flooding when starting the engine or black smoke on startup, decrease these values. An often overlooked effect of changing to larger injectors is that you'll spray more fuel during cranking. These values should all be adjusted down when changing to larger injectors (or use the compensation feature on Settings 5).  
  
_Inj vs Accel TPS1_  
\-These values are for fuel enrichment dependent on how fast you increase throttle. Here, a Setting value of 100 is equal to an INJ value of 1.000. The default settings show you that the faster you increase throttle, the greater the enrichment. Steady throttle (Input = 0) would have no enrichment. Most people leave the default values here, as I have done. If you wanted to alter this setting, I would suggest adjusting the Setting values while leaving the Input values alone.  
  
_INJ vs. TPS_  
\-These values are for fuel adjustments based on percentage of throttle. The default values give enrichment at higher throttle angles. Many people set these values all to 1.000, meaning that fuel settings are not dependent on throttle angle. This is done to eliminate variables when tuning. I am a big proponent of using this function and feel that it is a much better form of enrichment than using the INJ or Base Map to enrich at high loads. A reason to have enrichment at higher throttle angles is to be able to tune the car to run at stoichiometric (14.7:1) mixture at part throttle for maximum fuel economy and only run rich at full throttle when a richer mixture is needed. There are advantages to using this setting, particularly at part throttle, but using this function is very advanced. For one, it virtually eliminates the chance of running lean under load. In a sense, you are getting multiple INJ maps by using this function. In order to use the setting correctly, you'll need to determine the proper breakpoints for your car. On my car, WOT = 4.04v. Since TPS signal works off a 5v scale, WOT = 4.04/5 = 80.8% throttle. I would probably just bump 79.7% to the top value and put the setting at whatever my desired WOT AFR is. You would then need to figure out what your TPS voltage is at the maximum throttle you want to maintain stoichiometric at and set that percentage as your low limit with a setting value of 1.000. I figure this out by driving around (while logging) and only accelerating to what I feel the maximum throttle is where I would want to maintain stoichiomtric. Once you have your high and low limits for throttle enrichment, you can fill in your intermediate values as you see fit, either simply linear or by testing more throttle angles and deciding what you want the AFR to be under that condition. On my car, I set the maximum throttle for no enrichment as 30.5%.  
  
_Inj vs AirTemp_  
\-These values are just like the Water Temp Correction, but for air temp. The default values have a gradual leaning out of the mixture as the air gets hotter. Technically, correction for this is already handled by the MAFS, which directly measures air mass as it is affected by temperature and pressure, making this function redundant. But due to a lack of resolution in the map, you could still fall in the same load cell but need more/less fuel. Watch your AFR's on days with different temperatures to see if you feel this needs adjustment.  
  
_INJ vs Air Temp and Boost (max)_  
\-The name and available parameters are misleading. What this setting really does is INJ vs AirTemp (hot). The boost reference most likely does not mean anything, which is the popularly held opinion. What this means is that at some point, the car is considered to be "hot", at which point different air temperature corrections would come into play. There are setting values for Temp and Setting, with the setting value being the same as an INJ value. I have not had time to play with this setting, so I may add more to this later. The one interesting thing to note about this is that the lowest temperature set as a default is 60 C, which is much higher than anyone would actually ever see. Due to a lack of understanding, I simply leave the values at the default.  
  
_INJ vs Water Temp and Boost (max)_  
\-The same as the previous setting, except relating to water temperature.  
  
**Settings 3 Tab**  
  
The Settings 3 tab is used for the setup of the map and definitions of airflow curves. The screen will look like this:  


![fcedit-settings3](https://github.com/user-attachments/assets/5cb28446-42db-49d6-bb44-4b0fc3d8a952)

  
  
There are three setting boxes on this screen, explained below.  
  
_Map Reference_  
\-These settings define rpm and load breakpoints in your maps. A vast majority of users don't adjust these values, but there is a big advantage to doing so. You will see that the values in my table are nothing like those on a Monkeywrench map. Most maps will have rpm scaled in increments of 500 rpm up to 10,000 rpm. This is a wider range than the car will actually operate in and causes you to lose resolution by having cells that never get used. The same is true with the default load values. Only a high hp turbocharged car tht is maxing out the MAFS will see 19,000 load, and no car idles as low as 500 load. Advanced users will scale these values to concentrate points in their usable rpm/load range. To find out what that is, you need to look at idle and redline rpm, and idle load and maximum load. Once you find these four values, you can scale your maps correctly. The big downside is that once you do this, you will need to recalculate your entire map by hand due to switching all the load and rpm references, but the payoff is better resolution and more accurate tuning. I use an Excel spreadsheet to do this and will upload it once I get the final tweaks done to it.  
  
Finding out how your car behaves at idle is very important to setting these values. To do this you will want to make a log at idle from cold to fully hot and plot PIM (load) over the duration of this log. See this thread for more information on this procedure:  
  
[http://www.newcelica.org/forums/showthread.php?t=233154](http://www.newcelica.org/forums/showthread.php?t=233154)  
  
Using the example in the thread above, I found on that car that when fully cold, the initial load was around 1680 and dropped to around 1600 when fully warmed up. When the fans kicked on at 93C, you see a jump in load to 1700 and the idle pick up from 1000 to 1150. For load, these are the only two non-linear breakpoints I use. My lowest breakpoint would be 1600 and the second breakpoint would be 1700. All remaining breakpoints between that and my maximum load breakpoint I scale linearly. This makes it much easier to tune the map.  
  
On the subject of rpm breakpoints, I typically don't follow as rigidly linear of an approach. The PFC can extrapolate off the 20x20 grid, so there is no reason to set very high or low rpm breakpoints. In the example above, I would set my two lowest rpm breakpoints as 1000 and 1150 rpm. Remaining breakpoints would be spaced fairly evenly. I tend to like to concentrate rpm breakpoints somewhat closer at high rpm as tuning is more critical there and depending on how my math works out, I often set the highest rpm breakpoint lower than my indicated fuel cut.  
  
One other thing to note with a 2ZZ is cam (lift )transition. You will find that it is impossible to tune directly on the cam switch point, so setting an rpm breakpoint there is pointless. For maximum power, tuning just before and after lift transition is important. Once you determine your optimum lift transition point, you should place rpm breakpoints just to either side of that point. In my maps, I often use a tighter rpm breakpoint spacing (400 rpm) post-cam switch and a looser one before (450-500 rpm).  
  
_Air Flow_  
\-The airflow box lets you select five different airflow curves. Most people stick with the default airflow curve. The other setting is for airflow meter calibration. The default values are all 100.0 and 99% of people should leave them that way. The reason they exist is to recalibrate the airflow meter for being in a larger or smaller tube than stock. Airflow meters are calibrated to be in a certain size tube, and changing that sube size in any way will throw off this calibration. But the same effect can be achieved by altering the values in the Air Flow Curves box. Another possible reason to use these corrections would be if you were flowing enough air to max out the meter. You could increase the value for 5.12v to compensate for this, but this would be a rough fix at best.  
  
_Air Flow Curves_  
\-These show the the actual airflow associated with a given airflow meter voltage. Careful observation and things learned while tuning will show you that not the entire range is used. You'll notice that the bottom few points show 0 airflow, which makes them useless. My turbo GT-S will nearly max the meter, but an N/A car will not, and should be able to remove some of the high voltage points. Once you remove these points, you can add data points into a more critical area of the curve for better resolution.  
  
**Settings 4 Tab**  
  
The Settings 4 tab is basically a continuation of the Settings 2 tab. The screen will look like this:  
  
![fcedit-settings4](https://github.com/user-attachments/assets/1621574a-3e4b-439a-bc45-56a5978491c9)

  
There are seven setting boxes on the screen, explained below.  
  
_IGN vs WaterT_  
  
\-This setting is used to retard ignition timing on a linear scale once water temperature reaches a certain temperature. I've found that my 2ZZ will operate somewhere in the 83-86C range. I also found that even on the hottest summer day, siting in traffic, my car would not rise above 94 C. I left the retard at zero at the lower breakpoint. If you notice knock on a hot day or after the car sits in traffic and the water temperature rises, you can increase the retard at the upper limit to increase the ramp rate.  
  
_IGN vs WaterT Cool_  
  
\-This setting is used to retard ignition when the car is cold. Most people leave the default settings in place here. What the default settings are telling you is that once the car reaches 60 C water temperature, there is no longer any ignition retard.  
  
_IGN vs BatV_  
  
\-This setting is used to adjust ignition advance based on battery voltage. Most people leave these at the defaut values. That said, you should look at what your logged battery voltage is. I notice on my car that most of the time I'm seeing 13.7-13.8v, which will cause the car to run slightly more ignition advance than my map would indicate based on the default settings.  
  
_IGN Dwell vs RPM_  
  
\-This setting is used to adjust the dwell time in the ignition system dependent on engine rpm. Dwell is a term that technically relates to an old style of ignition, but the meaning is similar. Basically, the faster your engine spins, less time it takes for the piston to move up and down. Dwell measures how soon you need to start charging the ignition system to make a spark at the proper time. Since the time needed to charge up the ignition doesn't change as engine speed increases, you need to start that event sooner to compensate for the piston moving faster. I'm not aware of anyone who changes these settings from the default settings.  
  
_IGN vs AirT_  
  
\-This setting serves to retard ignition when air temperature gets very hot. I've noticed that the default settings require the air temperature to be very high before any ignition retard occurs. You should log some data in very hot temperatures and see what the maximum air temperature is in your logs. I lowered the breakpoints significantly below the default settings. My car seems to be unwilling to register air temps above 34 C. I have heard that Toyota had a large number of warranty claims for 2000-02 mass airflow meters (which contains the air temp sensor), so make sure you look at yours carefully.  
  
_Boost vs IGN S.F._  
  
\-What this stands for is Boost vs Ignition Scaling Factor. I'm not sure why this would be a linear scale from zero to one, or why the "boost" values of 3840 and 7936 repeat themselves in several spots. I have seen the value of 760 logged for boost in FC Edit. What this corresponds to is 760 mmHg, which is standard atmospheric pressure. Since the Celica does not use a MAP sensor, it makes sense that this value would be a constant 760. A pressure value of 3840 is roughly 5 Bar, five times atmospheric pressure or almost 50 psi boost. If that is the case, all these corrections for boost would never come into play. These values my purposely be set this way to make this happen.  
  
_IGN vs TPS_  
  
\-This setting is used to advance or retard ignition timing based on throttle position. Values above 1.000 will advance timing and values below will retard timing. The TPS values are percentages. The default values are all 1.000, and most people do not alter these values.  
  
**Settings 5 Tab**  
  
The Settings 5 tab is used for setup of the fuel injectors and custom features. The screen looks like this:  
  
![fcedit-settings5](https://github.com/user-attachments/assets/a39ffc56-8464-4d88-a758-d953145cb2b5)

  
There are four setting boxes on this tab, explained below.  
  
_Injectors_  
  
\-These values are used to make percentage based adjustments to individual injectors. This setting is used if you're switching to larger injectors. For instance, if you moved up to 550cc injectors from the standard 310cc GT-S injectors, your old injectors would only flow 56.4% as much fuel as your new injectors. You could enter 56.4 into the column on the left and not have to make any changes to your map. This setting will affect any settings in the PFC that deal with raw injection times: Base Map, cranking fuel settings and Accelerate Injector settings. This is a setting that I've changed my mind on as I've tuned more maps. Since it automatically adjusts for cranking and acceleration times, I really like to use this setting and leave the default settings in those areas alone.  
  
You can also use these settings for is to adjust for small variances from injector to injector. This would require that you have your injectors tested by an injection shop, and as long as you kept the injectors in order, you could adjust for the small variances in flow rate here. While you had your injectors at the shop, you can have them tested for lag time. The second column is to account for injector lag time variances, in milliseconds. Just as your injectors may flow slightly different amounts of fuel, they may also have slightly different lag times. If you have the stock injectors in the car, you should leave these values at the default values.  
  
_INJ Lag (mS) vs BatV_  
  
\-This setting is used to adjust the lag time of the injectors based on battery voltage. All injectors are rated for both flow rate and lag time at 14v. I have tried and been unsuccessful at finding lag times at various voltages. This is actually not a huge problem, since most cars run right around 14v anyways. Larger injectors will have longer lag times. What I did for my 630cc Mototron/MWR injectors is just take the rated lag time at 14v and divide it by the default value at 14v, giving me a percentage. I then multiplied that percentage through all the values at other rpms. I did this based on a guess that the lag curve would be the same shape for all injectors, but might be offset from injector to injector. Again, this is a guess but since the car typically runs very stable at 14v, that is the most critical value. The effect that the lag setting has on actual fueling is quite large. What it does is compensate for the fact that larger injectors take longer to open. As as example, if you doubled the size of an injector but kept the injector duration the same, you actually wouldn't get double the fuel. This is because more of the on-time is getting used up waiting for the injector to open, so you end up with less effective on-time with the larger injector. A secondary effect has to do with the timing of the injection. With a bigger lag setting, the injection cycle would start slightly earlier to get fuel spraying at the same time. This could possibly affect high rpm performance if fuel were spraying later than expected. If you've switched to larger injectors and then later correct this setting, you'll notice that the car will suddenly start running rich and that you need to decrease all the injection times. Again, if you have the stock injectors, leave this setting alone.  
  
_FC Box Custom Features (Key Off / Key On for changes to take effect)_  
  
\-These are somewhat advanced settings and do not apply to the Celica. Explaining their purpose is beyond the scope of this sticky.  
  
_Notes_  
  
\-You can enter notes here about your map. If you have evolutionary map development, you could note the changes made for the new revision.
