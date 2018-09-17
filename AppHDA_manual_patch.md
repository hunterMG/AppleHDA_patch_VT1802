# AppleHDA pacth
1. `ConfigData` -> 
    AppleHDA.kext/Contents/PlugIns/AppleHDAHardwareConfigDriver.kext/Contents/Info.plist/IOPersonalities -> HDA Hardware Config Resource -> HDAConfigDefault -> Item 0 这一项的子项：

    `ConfigData`: 如果没有这项则新建，类型为 Data; 如果已经有了，把上面的 ConfigData 填入；
    `CodecID`: 285639750 (VT1802)
    `FuncGroup`: 1
    `LayoutID`: 3

2. Platforms.xml.zlib
3. LayoutXX.xml.zlib (XX为ConfigData中的layoutID)
4. patch AppleHDA
    binpatch 或 Clover/config.plist/`KextsToPatch`
5. patch DSDT
    DTGP + `HDEF`'s _DSM
6. IRQ fix(laptop)
    Clover/config.plist
## post patch:
7. EAPD fix
    `CodecCommander`