Zwift Activity Monitor
======================

## The Power is Within You

This application allows Zwift users to monitor their moving average power and FTP in real-time.  It also provides valuable metrics to the rider such as average and normalized power (NP), intensity factor (IF), and training stress score (TSS).  For the racer and time-trialist, there's also the ability to configure distance based splits with optional goals.  And finally, you can time your own laps and segments (like Alpe De Zwift) using the laps feature.


![main_view](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitorV2/images/ActivityView.png)
#### Example of Main View window

![split_view](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitorV2/images/SplitView.png)
#### Example of Split View window

![lap_view](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitorV2/images/LapView.png)
#### Example of Lap View window

## How It Works

Zwift Activity Montitor (or ZAM for short), monitors outgoing network packets generated by the Zwift application and
aggregates the data into statistical moving averages.

The network packets that ZAM consumes contain some important values.  Some of them are:
* Current power output
* Current heartrate (if wearing an HRM)
* Distance travelled
* Time spent riding

## Prerequisites

Before you begin, ensure you have met the following requirements:
* Latest version of Npcap: Packet capture library for Windows. (https://nmap.org/npcap/#download)
* .NET5 Framework (Desktop, not Console)!

## Installing Zwift Activity Monitor (Windows Only)

Note: The Setup-ZAM.exe file is signed by a certificate.

To install Zwift Activity Monitor, follow these steps:

* Make sure you've installed the latest version of Npcap from the link above in Prerequisites.
* Download the latest Setup-ZAM.exe release from this GitHub repository.
* Run the installation.  The installation is signed, but you may still receive a popup from Windows SmartScreen.

## Using Zwift Activity Monitor

When you launch ZAM for the first time, you will be presented with the configuration window.  The following section describes this important step.

### Configuration

ZAM is easily configured via a set of configuration tab pages in the <b>Analyze->Options</b> dialog.

#### Options -> System Configuration Tab

ZAM first and foremost needs to know what network you use when running Zwift.  It's usually pretty simple as most
computers are either Wi-Fi or direct Ethernet cabled.  Within ZAM there is a packet monitoring system which MUST be started
in order to use ZAM.  This can either be done manually each time you run ZAM (by clicking the Start button), or by checking Auto-Start.

* Current User - The user profile that will be used during this ZAM session.  This defaults to the Default User Profile.
* Network - The network in your computer you use when running Zwift.
* Auto-Start - Whether to start the Zwift Packet Monitoring service automatically when ZAM starts.
* Window Position - Once you find where you like the ZAM window to sit, enter those coordinates and it will open there each time.

![system_options](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitorV2/images/SystemOptions.png)

#### Options -> User Configuration Tab

Multiple user profiles are ideal for multi-rider households, or if you'd like to be able to quickly select a different collector set. 
A default profile is provided for you, but you should configure it properly before using.

* Name - Identifies the rider.
* Weight - In Kilos or Pounds.
* FTP - From your last FTP test or the value that Zwift has.
* Email Address - This allows you to email yourself the rider recap sheet.
* Default moving average collector selection.

The moving average collectors selected will be shown by default for this user.  However, you can select different collectors from the main ZAM window. 

Note: <b>It is VERY important to set the weight and FTP fields properly!</b>  These are used to calculate Watts/Kilo and Intensity Factor.

![user_profiles](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/UserProfiles.png)

#### Options -> Collector Configuration Tab

ZAM uses moving average collectors to present statistics on the screen in real-time.  A collector has the following attributes:

* Time Duration - The period for which a collector retains data.
* Average Power display format - Moving average for all values currently in the collector.
* Maximum Power display format - The maximum value attained from the moving average.
* FTP display format - Maximum power value * 0.95 (Most applicable to the 20 minute collector).
  * Watts - Rounded to nearest whole number.
  * Watts/Kilo - Shown as #.## (i.e 4.12)
  * Hidden - Not shown.

![collectors](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/Collectors.png)

#### Options -> Splits Configuration Tab 

ZAM allows you to configure distance based splits to review your progress while riding.  Optionally, you can also configure goals so that you'll know if you're ahead or behind on your split times.  Customization of goals is also supported.  A split has the following attributes:

* Show Splits - When checked, the Splits View window will display automatically for 5 seconds when the distance is hit.
* Splits Every - This determines the distance (in km or mi) that splits occur.
* Calculate Goal - When checked, the splits view window will show a +/- indicator of your time vs the split time.
* Goal Time and Goal Distance - Together these are used to automatically calculate the number of splits and the target split times.

##### Customizing Splits

* If you've checked both the Show Splits and Calculate Goals checkboxes, you will have the option to edit the templated splits.  New splits can be added (at the end only), and existing splits can be edited or removed.  
* You can edit / save the bottom split goals grid as often as you like.  **Important Note: If you edit / save the upper split settings, any custom splits will be overwritten.**

An example of the Splits View window is shown at the beginning of this readme file.

![splits](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/Splits.png)

#### Options -> Laps Configuration Tab

ZAM allows you to perform lap and/or segment timing while riding.  Similar to Garmin head units, laps can be either manual or automatic.  If automatic, laps can be triggered by  distance, time, or position.   A lap has the following attributes:

* Measurement System
  * Imperial - Display in Imperial units.
  * Metric - Display in Metric units.
* Lap Style
  * Manual - Laps occur only on lap button press.
  * Automatic - Laps occur when pre-defined actions are triggered.
* Lap Trigger (applicable only when Lap Style is Automatic)
  * Distance - Lap occurs when specified distance is reached.
  * Time - Lap occurs when specified time has elapsed.
  * Position (multiple position waypoints may be set while riding).
    * Start and Lap button press - A waypoint occurs at the start and on each lap button press.
    * Lap button press only - A waypoint occurs only on lap button press.

![lapbuttons](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/LapViewControlButtons.png)
Use the control buttons on the Laps View window to:

* Lap - Completes current lap and starts a new lap.
  * Note: A waypoint is set if auto-lapping by position.
* Reset - Clears all laps and waypoints and starts a new lap.
  * Note: A waypoint is set if auto-lapping by position and the Start and Lap button press attribute has been selected.

An example of the Laps View window is shown at the beginning of this readme file.

![laps](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/LapConfig.png)

### Using While Zwifting

#### Quick Start

**Important Note: The activity monitor can only overlay Zwift if it (Zwift) is configured to run in windowed mode.**

* Start the Zwift Packet Monitoring service from the Analyze->Options System Tab by pressing Start.  Maybe while you're there select the Auto-Start option.
* Click Analyze->Start.
* Pedal away!
* Click Analyze->Stop when done.  A ride recap window will appear.

#### Timer Set-Up

If you've ever done a WTRL TTT then you know there's usually a delayed start after the banner drops. Or, maybe you're in an event pen and don't want to worry about clicking Analyze->Start when the banner drops.  We've got you covered! Setting the timer allows you to pre-determine the ZAM start time.  You set it up and a countdown begins.  When the countdown ends, the system "clicks" Start for you.

* Click Analyze->Setup Timer.
* Set your delay time.
* Click the Start Timer button.
* When the countdown ends, start pedalling!
* If you change your mind or need to reset the timer, Click Analyze->Stop Timer and repeat the setup process.

Timer behavior settings:
* Monitoring starts when event timer starts (default).
* Monitoring starts when countdown completes.
  * Note: This is when the WTRL begins its TTT timing.

![setup_timer](https://github.com/ruffk/ZwiftActivityMonitor/raw/master/ZwiftActivityMonitor/images/SetupTimer.png)

## Contributing to Zwift Activity Monitor

See the GitHub documentation on [creating a pull request] (https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).

## Credits

* Brad Walker for development of the ZwiftPacketMonitor library (https://github.com/braddwalker/ZwiftPacketMonitor) and giving me great ideas.

* Icons made by <a href="" title="photo3idea_studio">photo3idea_studio</a> from <a href="https://www.flaticon.com/" title="Flaticon">www.flaticon.com</a>

* Normalized Power®, Training Stress Score® and Intensity Factor® are registered trademarks of TrainingPeaks, LLC.

## Contact

If you want to contact me you can reach me at <mailto:ruff.kevin@outlook.com>.

## License

This project uses the following license: [MIT License] (https://github.com/ruffk/ZwiftActivityMonitor/blob/master/LICENSE).
