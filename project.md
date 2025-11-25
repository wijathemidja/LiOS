# Project Overview

## Hypervisor vs Emulation

Apple ended iOS support for hypervirtualisation in iOS 16. This means we have to use emulation (though see below for a 'possible' way to enable HyperV) 


### Emulation w/ Venus and VirGL
Based off UTM we can see that QEMU is the next best shot. However, if we want to use MoltenVK to render Vulkan, we need to use Venus. In essence, the virtual driver on the guest (Ubuntu 22.04+ / SteamOS 3 ARM (?)) will communicate with Venus through a QEMU bridge. Venus then talks locally with the host (our iDevice), and we use MoltenVK (Vulkan -> Metal API) to render it on the iDevice with hardware acceleration. Similar to Venus is VirGL, which would talk to AngleGL (which is already in UTM).


### Possible Hypervisor 
Recently, stossy11 (developer of MeloNX) has been working on maciOS. It can natively run macOS CLI apps through the iOS kernel (as they re both based off XNU). macOS already has kexts (kernel extensions) and entitlements to enable hyperv.

maciOS is **NOT AN EMULATOR** and so we can assume there is ahuge share of kernel code (XNU forks) between the macOS and iOS.

Either a full access jailbreak (not likely) or a way to use a Mac kext/entitlement on iOS (slightly more likely) would allow for HyperV and virtually no performance loss. 

TLDR : We need a way to access the kernel extensions and kernel and/or to sign/entitle the HyperV extension to LiOS. 

The second option is slightly more likely - the RAM entitlement can be given to sideloaded apps with the Get More RAM! app, but the RAM entitlement *IS* native to iOS (but we would usually have to sign the entitlement using XCode and a developer certificate). However, if the kernel has support for the kext (as macOS XNU does) we have a way for HyperV (and this is still compatiable on M and A series chips hardware-wise).

Also, on iOS 16 devices with Trollstore, Hyperv could work out of the box.

However LiOS would not require HyperV, if the emulation is optimised enough.