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

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/ac473ce4-7819-4026-ac05-58e2ae9f045e)

3. Double click the "Windows audio" service to open its properties. Go to the "Login" tab:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/47e0922c-2006-43b0-891c-5c41ac9843a0)

4. Select the upper option: **Local system account.**

Click OK.

Sound will not work on computer with this particular setting, **but we will be able at least to bring the "Windows audio" service up, with Webcam/Mic connected:**

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/76344d9e-8fde-4d16-8244-1bfdebbc093d)

5. Now back in the Services window, select again the "Windows audio" service, and click on **"Start the service"**

You shoud see the **"Windows audio" service UP (little speaker in task bar)**, and computer won't produce any sound (Again, this is normal, sound will come back after rollback later) :

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/29b9bd76-b74e-4689-9a7c-989e120a59c4)

6. Now Open Windows settings / sound page, and in the "Input Devices" list, click the Webcam Mic we need to disable effects on, as shown on first picture.

**Disable the "Audio enhencements" for it.**

Note that sliders might be at 0, but this is as expected and normal, sound is not operational:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/9747edda-3ae2-4658-a106-53995efeb558)

**Great. We have disabled the Audio enhancements for this Webcam Mic device.**

_Now close the Windows settings / sound page, otherwise it gets a bit messy when we will rollback and re-enable Audio on computer_

7. Now to **re-enable Audio**, a little bit more tricky

Open again the "Windows audio" service as done in step 3.

Go again to the Login tab.

This time, rollback to select the lower "This account" option.

You end up with a blank field:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/efdada85-d7d4-440e-bde8-2208eb20f764)

8. Click the "Browse" button to the right of the blank field. A new Window appears.

Click on **"Advanced" button: **

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/ee8bab15-2bf2-4250-ae1a-d69c317ba71d)

9. A new window appears again. Click the **"Search" button** to the right:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/063d3534-a3f3-4348-8b5a-e80d694f0b17)

10. You should see in the bottom pane, a choice of lines.

**IMPORTANT: Select the line: LOCAL SERVICE**

Then, click the OK button

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/2b440175-96be-4129-8ab4-479c4014bee4)

11. Back to the previous window, check that LOCAL SERVICE is selected, and click Ok again:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/69a09f41-e523-42a7-84a4-64d6fdb80b28)

12. Now back in the "Window audio" service "login" tab, **blank completly the 2 password/confirm fields**, remove all the stars which are in those 2 fields

Then click OK:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/37316689-d848-4d42-80de-962900b59ebd)

13. You should receive a Popup, saying that it will take effect after restarting the service.

Click OK:

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/2fdf5f69-2853-4695-937a-531458feea07)

14. Now let's restart the "Windows audio" service, to get sounds back!
**Do the same actions as in step 5**, select the "Windows audio" service, and click "restart" (Or right click on the "Windows audio" line and select "Restart"

![image](https://github.com/Pieloth/Webcam-mic-win-audio-crash/assets/73445512/edf43946-a546-40c7-b6be-19549cf82df0)

**ET VOILA !**

Sounds are back on computer, and Webcam + its Mic are now working (without the Audio enhancements option) !!!

You can check the volumes and test Mic by re-opening the Windows settings / sound page

**Note 1:** If you set back the "Audio enhancements" option to the Webcam Mic in Windows settings / sound, >>> BAMMM <<< , after restarting the "Windows audio" service or rebooting the computer, you will hit the same bug again!

**Note 2:** After some Windows update, the default setting "Audio enhancements" activated for Webcam Mic may come back. I experienced this a few days ago... alas, in this case, you will need to rerun this full procedure to disable it again.

Hope it helps!
