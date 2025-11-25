# LiOS (Linux for iOS)
A possible way to execute Linux applications on iOS devices. 

## How?

### Architecture
Linux has **native** ARM builds. Most notable for gaming is the upcoming SteamOS for ARM, which will be used on the Steam Frame, Ubuntu & Debian also already have native ARM64 builds.

This is important to iOS as modern iOS devices use ARM64 (well ARM64e). This means no emulation of the CPU is needed - which creates a performance overhead such as emulating a Switch.

### Hypervisor vs Emulation

Some (very little) games exist native for ARM but distros already have full basic support (see above). This means they can run through a hypervisor for iOS instead of an emulator, giving us much more performance. This will require JIT AND a hypervisor (see project.md) which can already be achieved on  iOS 16.3 and below  (See StikDebug / StikJIT + and UTM HV). We already have JIT on iOS 26, but require a hypervisor.  

For x86 software, FEX may be used. It is compatiable with Arch (which has a project called Arch ARM), the upcoming SteamOS-ARM, and currently Ubuntu since v22.04 . FEX is an emulator however, and so will have reduced performance. 

### Engine

As Linux native games don't use DirectX (which is why WINE is sometimes used) they either use OpenGL or Vulkan. Vulkan already has **NATIVE** iOS support through Metal (MoltenVK) - we already know this works well, as MeloNX uses it for Switch emulation. OpenGL ES 2.0 and most of 3.0 has support for Metal through MetalANGLE... but this is used in older games, and Vulkan would be preferable. 

For DirectX games DXVK with Wine could be used or Steam Proton.

## Basic Plan

Hypervisor setup (similar to UTM-HV) that runs Ubuntu prefernable with LXQt (as its lightweight) (or even no dedicated DE). The easiest way to do this would probably be to use Lubuntu. 
Automatically install Steam + FEX to this Ubuntu system.

When a Vulkan game runs, use MoltenVK to render it , using hardware acceleration of an A/M series chip, similar to how MeloNX runs. An alternative to this would be to render it in the VM using unofficial Vulkan SDK for ARM Linux (though an offical SDK exists for Windows on ARM)

