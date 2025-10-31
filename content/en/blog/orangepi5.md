---
title: "OrangePi 5"
date: 2025-10-19T13:14:54-05:00
draft: true
---

The original Raspberry Pi released on February 29, 2012 <sup>[1]</sup>, at an astounding $35 USD. A low cost, credit card sized computer redefined what was possible for educational computation and ignited innovation in homebrew, homelab, and hacker communities worldwide. 

Since then, copycat clones have pushed the form factors smaller, enhanced hardware capabilities, and added new features with every generation. By 2025, it's possible to get a full blown ARM64 server with enterprise features for under $500 USD. For example, the [Radxa Rock5 ITX+](https://radxa.com/products/rock5/5itxp).

In my homelab, I run a fleet of over 30 RK3588 boards from the Pine RockPro64 to the Orangepi5. Managing Kubernetes and building a Ceph cluster on these boards has been full of challenges, but also full of learning. Among them, my favorite board is the Orange Pi5 (v1.2). Let’s dive in.  

## Code

```python
import ttnn
ttnn.device()
```

```sh
curl http://localhost
```

## The Hardware

![OrangePi 5 Top Down](/images/2025/orangepi5-topdown.png)





## References

[1] [Raspberry Pi - Wikipedia](https://enwikipedia.org/wiki/Raspberry_Pi)