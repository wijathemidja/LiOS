# iHVx (iDevice Hypervisor for XNU)

Though a hypervisor is not needed for LiOS, it would be greatly benificial. I believe it is possible to create a driver which can completely bypass the use of KEXTs which would (probably) require a root jailbreak (or Trollstore on iOS 16).

DriverKit allows us to make drivers not just for macOS but also for iPadOS. With misaka26/mobileGesalt expolits we can already let iPad only apps work on iOS. 
DrvierKit also allows us to talk to kernel drivers, this may let us talk to graphics drivers for hw acceleration and make a 'dummy driver' that runs in userspace that communicates with official kernel drivers (that run in kernel space) to achieve virtualisation (ie the dummy driver would be a central communicator). 

DriverKit may not work on iOS. Currently only official support os for M-series chip iPads - this could be because they share the exact same architechture as Mac. MobileGesalt exploits may work, but DriverKit is probably locked down to kernel. 

However, even if only for M chip iPads, any hyprevisor driver development would be great.

