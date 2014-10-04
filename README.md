rt5572sta
=========

Fixes for rt5572 chipset driver tested with Linux 3.16.3 based on DPO_RT5572_LinuxSTA_2.6.0.1 Ralink Linux driver.

THe vendor driver for the rt5572 (rt5572sta) is unstable. I am spporting a wireless adatper TP-Link TL-WDN3200 on Linux.

This is work related to linux support for the O2 Joggler.

Linux joggler 3.16.3 #5 SMP Tue Sep 30 23:28:07 BST 2014 i686 i686 i686 GNU/Linux

TP-Link WDN3200 testing shows that there are frequent disconnects.

This is my attampt to solve these issues.

From the kernel log:

 kernel: [mAntCfgInit: primary/secondary ant 0/1  
 kernel: [mbAutoTxAgcG = 0  
 kernel: ---> InitFrequencyCalibration  
 kernel: InitFrequencyCalibration: frequency offset in the EEPROM = 44  
 kernel: <--- InitFrequencyCalibration  
 kernel: RTMPSetPhyMode: channel is out of range, use first channel=1  
 kernel: MCS Set = 00 00 00 00 00  
 kernel: <==== rt28xx_init, Status=0  
 kernel: 0x1300 = 000a4200  
 kernel: ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 141  
 kernel: ip_tables: (C) 2000-2006 Netfilter Core Team  
 kernel: ===>rt_ioctl_giwscan. 4(4) BSS returned, data->length = 790  
 kernel: ERROR!!! RTMPSetTimer failed, Halt in Progress!  
 kernel: ---> RTMPFreeTxRxRingMemory  
 kernel: <--- RTMPFreeTxRxRingMemory  
 kernel: RtmpAsicLoadFirmware: ver 21/21, sum cdf7/cdf7, mac cdf72100  
 kernel: NICLoadFirmware: firmware loaded already  
 kernel: <-- RTMPAllocTxRxRingMemory, Status=0  
 kernel: RTMP_TimerListAdd: add timer obj f1e7523c!  
 kernel: RTMP_TimerListAdd: add timer obj f1e75284!  
 kernel: RTMP_TimerListAdd: add timer obj f1e752cc!  
 kernel: RTMP_TimerListAdd: add timer obj f1e751f4!  
 kernel: RTMP_TimerListAdd: add timer obj f1e7511c!  
 kernel: RTMP_TimerListAdd: add timer obj f1e75164!  
 kernel: RTMP_TimerListAdd: add timer obj f1e3faf4!  
 kernel: RTMP_TimerListAdd: add timer obj f1e2f084!  
 kernel: RTMP_TimerListAdd: add timer obj f1e2f0d0!  
 kernel: RTMP_TimerListAdd: add timer obj f1e3fbe0!  
 kernel: RTMP_TimerListAdd: add timer obj f1e3fa64!  
 kernel: RTMP_TimerListAdd: add timer obj f1e3fb94!  
 kernel: -->RTUSBVenderReset  
 kernel: <--RTUSBVenderReset  
 kernel: BBP_R254 = 80  
 kernel: CfgSetCountryRegion():CountryRegion in eeprom was programmed  
 kernel: CfgSetCountryRegion():CountryRegion in eeprom was programmed  
 kernel: Key1Str is Invalid key length(0) or Type(0)  
 kernel: Key2Str is Invalid key length(0) or Type(0)  
 kernel: Key3Str is Invalid key length(0) or Type(0)  
 kernel: Key4Str is Invalid key length(0) or Type(0)  
 kernel: 1. Phy Mode = 0  
 kernel: 2. Phy Mode = 0  
 kernel: NVM is Efuse and its size =3c[3c0-3fb]  
 kernel: Power = a0a  
 kernel: Power2 = e0e  
 kernel: Power = a0a  
 kernel: Power2 = e0e  
 kernel: Power = a0a  
 kernel: Power2 = e0e  
 kernel: Power = b0b  
 kernel: Power2 = e0e  
 kernel: Power = b0b  
 kernel: Power2 = e0e  
 kernel: Power = b0b  
 kernel: Power2 = e0e  
 kernel: 3. Phy Mode = 0  
 kernel: [mAntCfgInit: primary/secondary ant 0/1  
 kernel: [mbAutoTxAgcG = 0  
 kernel: ---> InitFrequencyCalibration  
 kernel: InitFrequencyCalibration: frequency offset in the EEPROM = 44  
 kernel: <--- InitFrequencyCalibration  
 kernel: RTMPSetPhyMode: channel is out of range, use first channel=1  
 kernel: MCS Set = 00 00 00 00 00  
 kernel: <==== rt28xx_init, Status=0  
 kernel: 0x1300 = 000a4200  
 kernel: r8169 0000:01:00.0 eth0: link down  
 kernel: ---> RTMPFreeTxRxRingMemory  
 kernel: <--- RTMPFreeTxRxRingMemory  
 kernel: RtmpAsicLoadFirmware: ver 21/21, sum cdf7/cdf7, mac cdf72100  
 kernel: NICLoadFirmware: firmware loaded already  
 kernel: <-- RTMPAllocTxRxRingMemory, Status=0  
 kernel: RTMP_TimerListAdd: add timer obj f1e7523c!  
 kernel: RTMP_TimerListAdd: add timer obj f1e75284!  
 kernel: RTMP_TimerListAdd: add timer obj f1e752cc!  
 kernel: RTMP_TimerListAdd: add timer obj f1e751f4!  
 kernel: RTMP_TimerListAdd: add timer obj f1e7511c!  
 kernel: RTMP_TimerListAdd: add timer obj f1e75164!  
 kernel: RTMP_TimerListAdd: add timer obj f1e3faf4!  
 kernel: RTMP_TimerListAdd: add timer obj f1e2f084!  
 kernel: RTMP_TimerListAdd: add timer obj f1e2f0d0!  
 kernel: RTMP_TimerListAdd: add timer obj f1e3fbe0!  
   
 
