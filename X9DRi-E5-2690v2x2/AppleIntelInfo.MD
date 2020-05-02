Had to update following lines to be 0 to avoid immediate KP at kextload
```
#define REPORT_MSRS				0
#define REPORT_RAPL_MSRS		0 
```

```
AppleIntelInfo.kext v2.9 Copyright © 2012-2017 Pike R. Alpha. All rights reserved.
logIGPU..................................: 0
logCStates...............................: 1
logIPGStyle..............................: 1

Warning: Clover hw.busfrequency error detected : 17d78400

CPU Ratio Info:
------------------------------------------
Base Clock Frequency (BLCK)............. : 100 MHz
Maximum Efficiency Ratio/Frequency.......: 12 (1200 MHz)
Maximum non-Turbo Ratio/Frequency........: 30 (3000 MHz)
Maximum Turbo Ratio/Frequency............: 36 (3600 MHz)
P-State ratio * 100 = Frequency in MHz
------------------------------------------
CPU P-States [ 29 (30) ]
CPU C6-Cores [ 3 4 8 14 15 18 19 ]
CPU P-States [ 28 29 (30) ]
CPU C6-Cores [ 0 1 2 3 4 5 6 8 14 15 18 19 ]
CPU P-States [ (12) 28 29 30 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 14 15 18 19 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 14 15 17 18 19 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 17 18 19 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ]
CPU C6-Cores [ 0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 ]
CPU P-States [ (12) 27 28 29 30 ]
CPU P-States [ 12 25 27 28 29 (30) ]
CPU P-States [ (12) 25 26 27 28 29 30 ]
CPU P-States [ (12) 23 25 26 27 28 29 30 ]
CPU P-States [ (12) 23 24 25 26 27 28 29 30 ]
```