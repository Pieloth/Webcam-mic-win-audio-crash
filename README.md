# Webcam-mic-win-audio-crash
# Webcam Mic shutting down Windows audio service: Complete walkthrough workaround

For those impacted by the specific recent Windows 11 bug, due to **Webcam microphone devices making Windows audio service to crash...**

For instance, Logitech C920 or C922 Webcams

The root cause seems to be due to the "Audio enhancements" option, enabled for the Webcam Mic (in Windows settings / sound), leading currently "Windows audio" service to crash

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/596f4ba3-ace0-4559-94d1-65973eb8c0b6)

**Disabling this option is the Workaround solution here.**

The Webcam and its Mic will work fine again (without the "Audio enhancements"), but this is enough as a workaround solution, before a final Microsoft update fix brought to "Windows audio" service.

So the question is now: ***How can we disable this option for the Webcam Mic??***
* If you plug in the Webcam and let its Mic enabled, then Windows audio crashes, leading to Windows settings / sound page be empty with no devices shown
* If you disable the Webcam Mic device, in Device Manager, then it won't appear in Windows settings / sound page, thus not possible to disable its Audio enhancements option

**Here is the proposed walkthrough** that did work fine for me, using a **little trick**, to be able to change and disable the Audio enhancements option in Windows settings / sound page for the Webcam Mic:
* Plug in the Webcam and be sure to enable it in Device Manager. Windows audio service will then crash, as expected
* Change a particular setting in Windows audio service, and restart it. It will be able to start, but without sound in computer (this is intented and normal). However, it will be enough to have all audio devices shown in Windows settings / sound page
* Open Windows settings / sound page. Select the faulty Webcam Mic, and **disable its "Audio enhancements" option** (as in image above). Close Windows settings page (as sliders get messy after re-enabling Windows audio service later)
•	Go back to Windows audio service, and rollback the tweak modification, to re-enable sounds on computer. **This time, as the Webcam Mic has its "Audio enhancements" disabled, Windows audio service will run fine!**

**Let's go now through this walkthrough with some pictures:**

1. First, be sure Webcam Mic is enabled is Device Manager, if you previously disabled it. This will make your Windows audio service to crash, but this is normal for now

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/3a4d028e-d73f-40f8-8941-792d35a65cdc)

2. Open Windows services **(Win+R , type services.msc)** , and locate the "Windows audio" service in the list

3. Double click the "Windows audio" service to open its properties. Go to the "Login" tab:

4. Select the upper option: **Local system account.**

Click OK.

Sound will not work on computer with this particular setting, **but we will be able at least to bring the "Windows audio" service up, with Webcam/Mic connected:**

5. Now back in the Services window, select again the "Windows audio" service, and click on **"Start the service"**

You shoud see the **"Windows audio" service UP (little speaker in task bar)**, and computer won't produce any sound (Again, this is normal, sound will come back after rollback later) :

6. Now Open Windows settings / sound page, and in the "Input Devices" list, click the Webcam Mic we need to disable effects on, as shown on first picture.

**Disable the "Audio enhencements" for it.**

Note that sliders might be at 0, but this is as expected and normal, sound is not operational:

**Great. We have disabled the Audio enhancements for this Webcam Mic device.**

_Now close the Windows settings / sound page, otherwise it gets a bit messy when we will rollback and re-enable Audio on computer_

7. Now to **re-enable Audio**, a little bit more tricky

Open again the "Windows audio" service as done in step 3.

Go again to the Login tab.

This time, rollback to select the lower "This account" option.

You end up with a blank field:

8. Click the "Browse" button to the right of the blank field. A new Window appears.

Click on **"Advanced" button: **

9. A new window appears again. Click the **"Search" button** to the right:

10. You should see in the bottom pane, a choice of lines.

**IMPORTANT: Select the line: LOCAL SERVICE**

Then, click the OK button

11. Back to the previous window, check that LOCAL SERVICE is selected, and click Ok again:

12. Now back in the "Window audio" service "login" tab, **blank completly the 2 password/confirm fields**, remove all the stars which are in those 2 fields

Then click OK:

13. You should receive a Popup, saying that it will take effect after restarting the service.

Click OK:

14. Now let's restart the "Windows audio" service, to get sounds back!
**Do the same actions as in step 5**, select the "Windows audio" service, and click "restart" (Or right click on the "Windows audio" line and select "Restart"

**ET VOILA !**

Sounds are back on computer, and Webcam + its Mic are now working (without the Audio enhancements option) !!!

You can check the volumes and test Mic by re-opening the Windows settings / sound page

**Note 1:** If you set back the "Audio enhancements" option to the Webcam Mic in Windows settings / sound, >>> BAMMM <<< , after restarting the "Windows audio" service or rebooting the computer, you will hit the same bug again!

**Note 2:** After some Windows update, the default setting "Audio enhancements" activated for Webcam Mic may come back. I experienced this a few days ago... alas, in this case, you will need to rerun this full procedure to disable it again.

Hope it helps!
