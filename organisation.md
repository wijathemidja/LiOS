The LiOS Project requires many different components to work together. 

For anything to work we need a QEMU core. Then for hypervisor support for QEMU we need a virtualisation driver / kernel extension. Then we need a frontend for LiOS and code to run in the VM (or if emulated with no hypervisor, our 'machine').

The naming scheme for components is simple. iCOMPONENTx, where i denotes it is for iDevices, and x denoted it is built for XNU, the iDevice (and macOS, watchOS, tvOS, and watchOS) kernel.

The Hypervisor development can be found under iHVx.
The QEMU core development can be found under iQEx.
Frontend development can be found at iLix.

