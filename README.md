# Mixing an 11s Di2 Rear derailleur ( RD-6870 ) with a 10s Front derailleur ( FD-6770 ) and an external battery ( SM-BMR2 )

## Summary
You can mix a 10 speed Di2 Front Derailleur with an 11 speed Di2 Rear Derailleur and external Di2 battery, if you use old firmware versions. 

This guide explains for to get those old firmware versions installed, in case they were ( accidentally ) upgraded.

Disclaimer: no warranty, no nothing. It may end in tears with dead components. But it worked for me :)


## Definitions
FD: your 10 speed Front Derailleur. This was tested with the Ultegra FD-6770.

RD: your 11 speed Rear Derailleur. This was tested with the Ultegra RD-6870. Should work with DURA-ACE RD-9070 as well.

Battery: your external battery. This was tested with SM-BMR2. Technically we are not talking about the battery, but about the battery holder (which stores the logic board and firmware).

# Guide - Prerequisites

### Connecting your bike to your PC
You need to connect your Di2 system to your PC. 

Google how to do it in your specific case.

Personally, I disconnected my SM-EW67-A-E box at the handlebars, and connected a borrowed SM-EW90-A in its place. This I connected this via the SM-BCR2 to my PC

### Firmware files
The firmware version that worked for me is 2.2.3. 

Shimano unfortunately no longer offers these files, but you can get them from [this forum post](https://www.bicycles.net.au/forums/viewtopic.php?p=1380200#p1380200). You need the zip folder "2.2.3 FW.zip".

### Shimano E-Tube Project
Download the oldest Shimano E-Tube Project you can get away with. 

* Major version 5 is available on [Shimano's website](https://bike.shimano.com/en-EU/e-tube/project.html)
* Major version 3 and 4 are available on [Shimano's website](https://bike.shimano.com/en-EU/e-tube/project/archive.html). 
* Major version 2 is available from [this forum post](https://www.bicycles.net.au/forums/viewtopic.php?p=1380200#p1380200).

You may have to download and uninstall/reinstall a couple of versions to see which version is right for you.

# Guide - Applying an old firmware version
Now to the fun and dangerous part.

Reminder that this is not officially supported and you may brick your devices.

## Downgrading your external battery ( SM-BMR2 )

If you have already accidentally upgraded your external battery, you need to downgrade it back to version 2.2.3.

This is however not officially supported, so we need to mess with version numbers to get this to work.

First, check in the E-Tube Project what the current version of your battery is.

Let's assume your battery firmware version is currently on 3.0.11.

We need to trick the E-Tube Project into thinking that the 2.2.3 firmware file is actually a newer version than 3.4.5, so that E-Tube Project will suggest that you upgrade to this "new" version.

The firmware version files that E-Tube Project uses are located at `C:\ProgramData\E-tube Project\FW`.

In that folder, search for the .dat file that corresponds with your battery, meaning that the file name starts with the part number ( eg `SMBMR2.3.0.11.dat` ).

Note that the file name contains a version number `3.0.11`.

We will place our the old firmware file here (as downloaded before from the forum post), but rename its file name so that is has a version number that is higher than the current firmware version number (so `3.0.11` becomes `3.0.12`). 

In other words: we take the `SMBMR2.2.2.0.dat` file that we downloaded, we rename it to `SMBMR2.3.0.12.dat` and we copy it into the directory `C:\ProgramData\E-tube Project\FW`.

Now we restart the E-Tube Project and we are prompted with the suggestion to update the battery to version `3.0.12`.

Perform the upgrade. 

Note that of course this is actually a downgrade to the actual `2.2.0` version.

After the upgrade is completed, the version on the battery should now be `2.2.0`. You should be able to verify this in the E-Tube Project.

Note that the E-Tube Project will now keep prompting you to update it again (because the current version of the battery is `2.2.0` and the latest version is `3.0.12`), but we can safely ignore it.

## Downgrading your rear derailleur ( RD-6870 / RD-9070 )

To downgrade your rear derailleur, follow the analogue steps as described for downgrading your battery.

One extra caveat is that the downloaded firmware files do not contain a .dat file specifically for the RD-6870.

You can use the file `RD9070.2.2.0.dat` instead. This is the Dura-Ace rear derailleur but its firmware version also works for the RD-6870 Ultegra rear derailleur.





That's it, hope it works for you!

### Sources
https://www.bicycles.net.au/forums/viewtopic.php?t=90499 Forum thread regarding Downgrading Di2.
