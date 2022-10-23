---
title: "Carbonfree"
date: 2022-04-27T23:07:28-05:00
draft: true
---

Zero Carbon Emission Mini Datacenter Lab
22U Rack Enclosure

[ 1U TOR switch w/ PoE ] 300W @ 110V
[ 2U 14X Raspi Cluster ] 14 X 8GB   : 112GB Ram
[______________________] 14 X 4Core : 56 Cores
[ 2U 14X Raspi Cluster ]
[______________________] 210W @ 110V
[ 2U 14X Raspi Cluster ] 
[______________________] 500GB X 14 =  7TB
[ 2U 14X Raspi Cluster ] 1TB   X 14 = 14TB
[______________________] 2TB   X 14 = 28TB
[ 2U 14X Raspi Cluster ] 4TB   X 14 = 56TB
[______________________] 8TB   X 14 = 112TB
[ 2U 14X Raspi Cluster ]
[______________________]
[   2U 14X Rock64Pro   ] 14 X 4GB   : 56GB
[______________________] 14 X 6Core : 84 Cores
[   2U 14X Rock64Pro   ] 
[______________________] Only PoE Splitters available - A cabling nightmare at scale
[       EMPTY          ]
[       EMPTY          ]
[______________________]
[ 3U EG4 48V 100Ah Bat ] - https://signaturesolar.com/eg4-lifepower4-lithium-battery-48v-100ah/
[                      ]   48V x 100Ah = 4800Wh or 4.8kWh
[______________________]   Has BMS
+                      -

## Current status

[ 1U TOR switch w/ PoE ] 300W @ 110V
[    2U 3X Raspi 4B    ] 3 X 8GB   : 24GB Ram | 3 X 4Core : 12 Cores
[______3X_Rockpro64____] 
[                      ] Pi consumption: 
[______________________]    9.4W X 3: 30W
[                      ] Rockpro64 consumption:
[______________________]    15W X 3: 45W
[                      ]
[______________________] Total: 
[                      ]    375W /hr  worst case
[______________________]     9kWh/day worst case
[                      ]
[______________________]    100W /hr  swag
[                      ]   2.4kWh/day swag
[______________________]
[                      ] 
[______________________] 
[       EMPTY          ]
[       EMPTY          ]
[______________________]
[ 3U EG4 48V 100Ah Bat ] - https://signaturesolar.com/eg4-lifepower4-lithium-battery-48v-100ah/
[                      ]   48V x 100Ah = 4800Wh or 4.8kWh (5120Wh / 5.12 kWh)
[______________________]   Has BMS
+                      -

Separate Rack for Power? https://www.youtube.com/watch?v=flJHA5_yYAg

If the 300W switch were to run for a few rainy days, we'd need potentially 300W X 72hours for up to 21.6kWh

ARM64 or RISCV?
https://riscv.org/wp-content/uploads/2018/07/Shanghai-1325_GreenWaves_Shanghai-2018-MC-V2.pdf

PoE Hat consumption: 5V @ 2.5A (15W)
Cluster wide: 70V @ 2.5A (210W)
                                                                      [   INVERTER  ]
     /------------------|              /------------------|           [             ]
    /  /   /   /   /   /|             /  /   /   /   /   /|           [             ]
   /__/___/___/___/___/ |            /__/___/___/___/___/ |           [             ]
  /  /   /   /   /   /  |           /  /   /   /   /   /  |              |       |
 /  /   /   /   /   /   |          /  /   /   /   /   /   |              +       -
/__/___/___/___/___/____|_________/__/___/___/___/___/____|______________[       ]


4 X 450W Renology in Series to hit > 60V (12V X 4)

https://www.homedepot.com/p/Renogy-450-Watt-Monocrystalline-Solar-Panel-2-Pieces-RSP450D-120x2-US/320645971


# Solar System

Metrics https://github.com/SunVibeCity/metrics

https://www.youtube.com/watch?v=adFGmOlDM-Y

https://github.com/mkaczanowski/packer-builder-arm