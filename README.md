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

1. Open Windows services **(Win+R , type services.msc)** , and locate the "Windows audio" service in the list
