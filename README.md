# Ubuntu Hard-freeze-fix

if you have just installed the Ubuntu on your and it’s freezes right at the login page or right after you logged in or it freezes at the start and capslock blinks aggressively then follow step by step procedure given below

step 1

Access Grub Menu

To access the grub menu restart your computer and as soon as your computer logo arrives keep clicking on esc it will open up the grub menu

Now click on the advanced ubiubtu option

click on network (will connect with your internet)

click on the dpkg (This command tells Ubuntu, *"Hey, look through all the software I've been trying to install lately. If any of it is half-finished, broken, or conflicting, fix the connections."*)

now you’ll have the boot option click on it 

This will fix the problem for the time being  from here will go to step 2

step 2

Turn of all the power saving feature your graphic driver and power management might be causing issue 

Open your terminal type sudo nano /etc/default/grub

Edit this line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash” to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force i915.enable_psr=0 i915.enable_dc=0”

### Why combine them?

- **`acpi=force`**: Ensures the motherboard follows Ubuntu's instructions for power-down and rebooting.
- **`i915.enable_psr=0`**: Stops the graphics driver from trying to "save power" on the screen—which is the #1 reason the 7490 freezes during use.
- **`i915.enable_dc=0`**: Disables "Deep Power Down" states for the GPU that can also cause the system to lock up.

Save and exit (`Ctrl+O`, `Enter`, `Ctrl+X`).

now sudo update-grub

rebbot your laptop
