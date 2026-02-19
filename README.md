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
