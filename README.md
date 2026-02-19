# Ubuntu Hard-Freeze Fix (Intel i915 Graphics)

If you have just installed Ubuntu and it freezes at the login page, immediately after logging in, or at startup with an aggressively blinking **CapsLock** light, follow this step-by-step procedure to stabilize your hardware.

---

## Step 1: Access the GRUB Menu (Temporary Workaround)
Use this step if you are currently locked out of your system and cannot reach the terminal.

1. **Restart** your computer.
2. As soon as the manufacturer logo appears, tap the **`Esc`** key repeatedly to open the **GRUB menu**.
3. Select **Advanced options for Ubuntu**.
4. Select the entry ending in **(recovery mode)**.
5. Select **Network** from the list (this enables internet access for repairs).
6. Select **dpkg**.
   > **What this does:** This command tells Ubuntu to "Look through all the software I've been trying to install lately; if any of it is half-finished, broken, or conflicting, fix the connections."
7. Once finished, select the **Resume** or **Boot** option to enter the OS normally.

*This will fix the problem temporarily so you can move to the permanent fix in Step 2.*

---

## Step 2: Disable Power Saving Features (Permanent Fix)
System freezes on Intel-based laptops (like the Dell Latitude 7490) are often caused by aggressive power-saving states in the graphics driver.

1. Open your terminal and run:
   ```bash
   sudo nano /etc/default/grub
2. Locate the following line:
   ```bash
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

3. Change it to:
   ```bash
   GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force i915.enable_psr=0 i915.enable_dc=0"

4. Save and Exit:
   ```bash
   Ctrl + o then Ctrl + x

5. Apply Changes:
   ```bash
    sudo update-grub

6. Reboot your laptop to complete the fix.

Now hopefully it Should be working

Why combine these parameters?

 acpi=force: Ensures the motherboard follows Ubuntu's instructions for power-down and rebooting.

 i915.enable_psr=0: Disables Panel Self Refresh. This stops the graphics driver from trying to "save power" on the screen—the primary cause of freezes on the 7490 model.

 i915.enable_dc=0: Disables Deep Power Down states for the GPU that can cause the system to lock up.
