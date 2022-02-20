# virtualboxConfigurator.bat
Asks the user about the virtualmachine to apply settings to and applies a list of settings used for installing MacOS Catalina.

Usage virtualboxConfigurator.bat "NAME OF VIRTUALMACHINE" 

// Changes some hardware settings to match Apple hardware
VBoxManage.exe modifyvm %1 --cpuidset 00000001 000106e5 00100800 0098e3fd bfebfbff
VBoxManage setextradata %1 "VBoxInternal/Devices/efi/0/Config/DmiSystemProduct" "iMac11,3"
VBoxManage setextradata %1 "VBoxInternal/Devices/efi/0/Config/DmiSystemVersion" "1.0"
VBoxManage setextradata %1 "VBoxInternal/Devices/efi/0/Config/DmiBoardProduct" "Iloveapple"
VBoxManage setextradata %1 "VBoxInternal/Devices/smc/0/Config/DeviceKey" "ourhardworkbythesewordsguardedpleasedontsteal(c)AppleComputerInc"
VBoxManage setextradata %1 "VBoxInternal/Devices/smc/0/Config/GetKeyFromRealSMC" 1

//Changes the default resolution to 1080p.
VBoxManage setextradata %1 VBoxInternal2/EfiGraphicsResolution 1920x1080

//Disables certain CPU features
VBoxManage setextradata %1 VBoxInternal/CPUM/IsaExts/AVX 0
VBoxManage setextradata %1 VBoxInternal/CPUM/IsaExts/AVX2 0
