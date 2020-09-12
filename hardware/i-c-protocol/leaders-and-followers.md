---
description: Devices on an I2C bus
---

# Leaders & Followers

Devices on the I2C bus are either **leaders** or **followers**. 

The **leader** device drives the SCL \(clock line\), which initiates the transmission of data across the SDA \(data line\) bidirectionally: either from the leader to the follower or from the follower to the leader. This meas that a **follower** device cannot initiate communication across the bus.

⚠️ **Old Terminology** — In antiquated texts, you may see leader devices referred to as _"masters"_ and follower devices refrerred to as _"slaves."_

There are often many followers connected to an I2C bus, but most often only one leader. It is possible to configure a bus to have multiple leaders. In this scenario, only one leader can control the SCL \(clock line\) at a time. 

⚠️ **Multi-Leader I2C** — ****At the time of writing, I have not come into a situation that has called for using multiple leaders on an I2C bus, therefore, I have not researched this configuration at length.



