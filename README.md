# jg_maker_magic_v03_bltouch

***

Modified Marlin firmware and adds the ability to use the BLTouch or clones on the JGMaker Magic 3D Printer.

# Installation

***
### Board modifications

If you have not already followed the guide to modify your board to add the ability to use the BLTouch or clones please do so [here](https://cnorton-webdev.github.io). You will need to do these modifications as without them there is no place to plug the probe into for the servo control signal. **Please note this will most likely void your warrenty with JGMaker**, so only do this modification if you are OK with doing so. Modification is relatively straight forward if you already know how to solder, if you do not know how to solder I would recommend finding a friend or someone who can help you with the soldering portion of the modification.

### First method

If you need to modify your probes offsets (recommended to tailor these to your machine) do not use this method! Included in the Marlin folder is the compiled binary *JG_Maker_Magic_V03.hex* which can be uploaded using any 3D Printer firmware update tool. This method uses offsets from using my BLTouch mount for the JGMaker Magic. If you are not using that mount or would prefer to verify and input your own probe offsets, please use the second method below after modifying the *Configuration.h* file with your offsets. For information on the area you would need to modify, see the section [Modifying Probe Offsets](https://github.com/cnorton-webdev/jg_maker_magic_v03_bltouch#modifying-probe-offsets).

### Second method

Download the Arduino IDE located [here](https://www.arduino.cc/en/Main/Software), upon downloading and installing the software, in the Marlin folder double click on the *Marlin.ino* file. Once the program loads, on the top click on Tools then Board and select Arduino Mega or Mega 2560. Under tools again, select Port and then choose the COM port that is your 3D printer. Click on the check mark to verify the code, once it is verified click on the arrow next to the checkmark to upload the firmware to your 3D printer.

# Modifying Probe Offsets

***

If you are not using my BLTouch mount for the JGMaker Magic or you want to use your own measured offsets you will need to edit the file *Configuration.h* located inside the Marlin folder. On lines 779, 780 and 781 in this file you will see

`#define X_PROBE_OFFSET_FROM_EXTRUDER 46  // X offset: -left  +right  [of the nozzle]`
`#define Y_PROBE_OFFSET_FROM_EXTRUDER 14  // Y offset: -front +behind [the nozzle]`
*Note that above these are a handy ASCII diagram.*

A negative number means the probe is located *left* of the nozzle for X and Y, below the nozzle for Z while a positive number means the probe is located ***right*** of the nozzle or above the nozzle. For the Z probe offset you will need to make sure you measure with the probe deployed. After measuring the offsets of the location of your probe in the X, Y and Zplanes, change the values to reflect your measurments. Save your changes to this file and follow the directions under [Installation](https://github.com/cnorton-webdev/jg_maker_magic_v03_bltouch#installation) using the second method to update the firmware.

# Testing

First, be ready to quickly unplug or turn off your printer in case the nozzle is going to crash into the bed!! This is important as you can damage your printer and your probe. Raise the Z axis to about 100, this will give you enough time to catch the printer if it is going to crash because of probe failure. On the LCD goto Prepare -> Auto Home and watch to make sure your probe deploys when homing the Z axis, and then watch and be ready in case it crashes. If the probe triggers successfully you're good and if it fails double check your Z connection and try reversing the wires, also verify your connection to the Y+ pins is correct and try again. 

# Setting Probe Z Offset

The best way to properly set your probe Z offset is in a guide by Joseph Cowdell which can be read [here](https://www.webcarpenter.com/blog/162-3D-Print---How-to-calibrate-Z-offset-with-a-BLTouch-bed-leveling-probe-sensor). I highly recommend following his guide to set your probe Z offset. Without doing this step you will most likely end up printing in the air.

# Contributing

***

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change. 

Please note we have a code of conduct, please follow it in all your interactions with the project.

## Pull Request Process

1. Ensure any install or build dependencies are removed before the end of the layer when doing a 
   build.
2. You may merge the Pull Request in once you have the sign-off, or if you 
   do not have permission to do that, you may request the reviewer to merge it for you.

## Code of Conduct

### Our Pledge

In the interest of fostering an open and welcoming environment, we as
contributors and maintainers pledge to making participation in our project and
our community a harassment-free experience for everyone, regardless of age, body
size, disability, ethnicity, gender identity and expression, level of experience,
nationality, personal appearance, race, religion, or sexual identity and
orientation.

### Our Standards

Examples of behavior that contributes to creating a positive environment
include:

* Using welcoming and inclusive language
* Being respectful of differing viewpoints and experiences
* Gracefully accepting constructive criticism
* Focusing on what is best for the community
* Showing empathy towards other community members

Examples of unacceptable behavior by participants include:

* The use of sexualized language or imagery and unwelcome sexual attention or
advances
* Trolling, insulting/derogatory comments, and personal or political attacks
* Public or private harassment
* Publishing others' private information, such as a physical or electronic
  address, without explicit permission
* Other conduct which could reasonably be considered inappropriate in a
  professional setting

### Our Responsibilities

Project maintainers are responsible for clarifying the standards of acceptable
behavior and are expected to take appropriate and fair corrective action in
response to any instances of unacceptable behavior.

Project maintainers have the right and responsibility to remove, edit, or
reject comments, commits, code, wiki edits, issues, and other contributions
that are not aligned to this Code of Conduct, or to ban temporarily or
permanently any contributor for other behaviors that they deem inappropriate,
threatening, offensive, or harmful.

### Scope

This Code of Conduct applies both within project spaces and in public spaces
when an individual is representing the project or its community. Examples of
representing a project or community include using an official project e-mail
address, posting via an official social media account, or acting as an appointed
representative at an online or offline event. Representation of a project may be
further defined and clarified by project maintainers.


### Attribution

This Code of Conduct is adapted from the [Contributor Covenant][homepage], version 1.4,
available at [http://contributor-covenant.org/version/1/4][version]

[homepage]: http://contributor-covenant.org
[version]: http://contributor-covenant.org/version/1/4/

# Credits

***

This firmware builds on the custom firmware by DaHai Zhu 
- [DaHai Zhu's original firmware](https://www.dropbox.com/sh/v7w7u2kmo34kw3u/AAAkNOoAhwuS59cOvrLWS9fDa?dl=0)