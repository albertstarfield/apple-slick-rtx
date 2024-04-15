# Slick Apple-Slick-RTX Journey

## Apple Slick RTX Project Rundown

So, the big question: "Is that a UTM Windows 11 x64 VM running Vulkan (with GPU Acceleration) and an RTX 3090 on Apple Silicon?"

Well, the answer's a confident **"Yes"**! We're just taking challenge about the argument that Apple Silicon will never get eGPU support. 

![Image](https://raw.githubusercontent.com/albertstarfield/apple-slick-rtx/main/images/scr5.jpg) 

## Section I: Current Community Image/Paradigm

### Apple Silicon, eGPUs, and the Real Deal

Ever wonder if Apple Silicon laptops might get a boost with eGPU support? Sorry, kid, but the answer from the community is a resounding **"NO"**. 

- [Reddit: MacGaming](https://www.reddit.com/r/macgaming/comments/18uibpi/will_egpu_ever_come_to_apple_silicon/)
- [Apple Discussions](https://discussions.apple.com/thread/255161653?sortBy=best)
- [Reddit: MacBookPro](https://www.reddit.com/r/macbookpro/comments/wj36e1/is_there_still_hope_for_egpu_support_in_apple/)
- [Reddit: OpenBSD](https://www.reddit.com/r/openbsd/comments/1av6spr/egpu_support_im_planning_on_buying_mac_m3_in_the/)
- [Apple Discussions](https://discussions.apple.com/thread/254022132?sortBy=best)

### The eGPU/GPU on mac Conundrum

Apple's latest macOS kernel and Nvidia? Forget about it. No Nvidia support for the latest gear—only AMD on Intel Macs.

[Apple eGPU Support](https://support.apple.com/en-us/102363#:~:text=eGPUs%20are%20supported%20by%20any,the%20software%20on%20your%20Mac.&text=View%20the%20activity%20levels%20of,choose%20Window%20%3E%20GPU%20History.)

### The UTM & qemu ( Upstream Qemu )

UTM/qemu doesn't play nice with GPU 3D acceleration for Windows. You can check out the source:

- [UTM Issues](https://github.com/utmapp/UTM/issues/3293)
In this issue forum and im quote "No, there is no way, nor any work to bring DirectX accelerated graphics to it being made. It is what it is. Sorry to put down your hopes for it."

Somebody did try working on a 3D driver fork, but the journey is long and uncertain. Check out the pull request [here](https://github.com/virtio-win/kvm-guest-drivers-windows/pull/943).

## Section II : Absurd Choices and the Mission

### What can we do and its result?

We forged ahead with some wild ideas. Connecting an Nvidia RTX 3090 seemed crazy, but hey, nothing's too absurd around here. 

KVM's PCIe passthrough, Intel/AMD x64 MMIO support, and a lot of other tinkering required—check out [this guide](https://github.com/lateralblast/kvm-nvidia-passthrough). Let's just say this involved some intricate steps.

Normal isn't on the menu in our realm.

### Juice-Labs and the AI World

Albert/Wahyu one of the Project-Zephyrine AI Programmer and professional AI engineer Willy know Nvidia's the name of the game when it comes to AI training and most of the AI inferencing hardware. 

Albert, with his J414 Laptop and Rhodes Chop ARM chip, is all about universal AI Inference Interface development. Willy's got his RTX 3090 for some serious model training.

AI training on Apple Silicon? Tough nut to crack, especially with the lack of Nvidia support. But the motivation to bridge the gap was strong.

### Networking and Challenges

Albert and Willy live far apart, so they worked with limited networks and a consumer-grade connection. But hey, they got creative with Tailscale solution tunneling.

Willy's got his i3-13th Gen RTX3090 hosted on Ubuntu with Juice Server running smoothly. Bandwidth varies between the two, but the mission's on track.

![Image](https://raw.githubusercontent.com/albertstarfield/apple-slick-rtx/main/images/scr6.jpg)

![image](https://raw.githubusercontent.com/albertstarfield/apple-slick-rtx/main/images/scr2.png)

### Windows 11 x64 Instance Connection

Connected the x64 Windows 11 local instance Apple Silicon to the server, and voila! Things rolled smoothly. Using x64 was crucial since other architectures encountered library load failures.

But here's the kicker—some glitches with Blender and memory translation issues. Sometimes the VM instance got weird, and Blender would crash and spit out some strange crap.

![Image](https://raw.githubusercontent.com/albertstarfield/apple-slick-rtx/main/images/scr3.png)

![Image](https://raw.githubusercontent.com/albertstarfield/apple-slick-rtx/main/images/scr4.png)

## Project Name: Apple-Slick-RTX

Why the name? Apple Silicon, pun of "slick," and a low-profile project running smooth as silk. Plus, the Nvidia RTX connection.

That's the lowdown on our journey. If you need more details or want to chat, hit up me [Albert/Wahyu](https://github.com/albertstarfield) or [Willy030125](https://github.com/willy030125).
#### Sidenote:
> There's a reason why using Whole x64 emulation, is because the program relies on a familiar x64 memory address it seems thus using Windows on Arm or Linux using Rosetta/Box64/Fex-Emu cause a library load fail (Image coming soon).

![image](https://raw.githubusercontent.com/albertstarfield/apple-slick-rtx/main/images/scr1.png)

> This solution won't show up the GPU on Task manager or Device manager, since its Application specific GPU acceleration not system-wide
