# Jammertest Hardware Deployment

This describes the GNSS-Lab hardware deployment for Jammertest 2025.
It focuses on provisioning hardware for the parameters as outlined in the experiment plan.

## GNSS Modules to be used

* There will be two sides with identical hardware: ("Car", "Bleik community house")
* There will be 8 GNSS modules on each site meaning 16 modules in total
* Dual-Band GNSS modules will be RM505Q-AE
* Single-Band GNSS modules will be MC7455

## Nodes in use

* (TBD) 3x Celerway Arcus Boxes (4125, 7065, 6361), having 2x dual-band modules each
* 1x Banana Pi R4 ("betterway"), having 2x dual-band modules
* 4x PC-Engines APU Box ("red box"), having 2x MC7455 modules each

## Hardware Overview

### Side: Car

| Name      | Platform | IP-Address    | Modules      |
| ========= | ======== | ============= | ============ |
| alidade   | APU      | 198.19.250.1  | 2x MC7455    |
| barometer | APU      | 198.19.250.2  | 2x MC7455    |
| kamal     | Arcus    | 198.19.250.11 | 2x RM505Q-AE |
| loadstone | Arcus    | 198.19.250.12 | 2x RM505Q-AE |



### Side: Bleik Community House

| Name        | Platform | IP-Address    | Modules      |
| =========== | ======== | ============= | ============ |
| chronometer | APU      | 198.19.250.3  | 2x MC7455    |
| dipcircle   | APU      | 198.19.250.4  | 2x MC7455    |
| nocturlabium| Arcus    | 198.19.250.13 | 2x RM505Q-AE |
| uranometria | BPI      | 198.19.250.21 | 2x RM505Q-AE |

### Consideration

There is apparently no use for the BG96 and the internal receiver in the celerway nodes. One could use them instead of one APU box.
It is not in use to keep the hardware setup as simple as possible and limit the number of model-types.

We plan to take three Celerway Arcus nodes - however, this may change due to availbility.