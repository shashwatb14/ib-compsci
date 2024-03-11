# Rescue Robots

## Important links:
- [Actual case study](./rescue_robots.pdf)
- [Computer Science wiki for vocabulary](https://computersciencewiki.org/index.php?title=2024_case_study)

## Overview

1. [Scenario](#scenario)
2. [Problems to be addressed](#problems)
3. [Technologies](#tech)
    1. [Computer vision](#cv)
        1. [Visual simultaneous localization and mapping (vSLAM)](#vslam)
        2. [Pose estimation](#pose-estimation)
4. [Social and ethical issues](#issues)
5. [Further research](#research)
6. [Challenges faced](#challenges)
7. [Additional terminology](#terms)

## <a id="scenario"></a> Scenario

- **BotPro**:
    - Company that makes robots for various industrial applications
    - Focus shifted to making **rescue robots**

- **Rescue robots**:
    - Designed to help with the search and rescue of humans after a **disaster** (like earthquakes and tsunamis)
    - Assist the efforts of rescue teams by **searching** and **mapping** areas, assessing damage, removing debris, delivering supplies, and evacuating casualties

- Found to perform below expectations when sent into a large factory after a fire and another factory that was damaged by an earthquake

- Robot had trouble **navigating the factories** and **reaching the exact location of survivors**

- However, operation was successful when deployed in a stadium after strucutural damage

- Root cause was the accuracy and difference  of the [`global positioning system (GPS) signal`](#gps) inside the factories
    - Strength of the satellite signal received was **insufficient**, resulting in errors in calculating robot's exact location
    - Factories were also an **unknown environement** to the robot
    - Damage caused meant that the **layout of the factories was different to any floor plans that existed**

## <a id="problems"></a> Problems to be addressed

- Redesgining of robot with the capability to **explore**, **map**, and **survey the interior of unknown and damaged buildings**

- Must be **cost effective** and focus on the new design was on **building efficient algorithms** to **improve robot performance** and not on the mechanical components

1. `Accurate mapping of the area`: robot needs to find its way inside buildings and reliably operate in a [`GPS-degraded environment`](#gps-degraded) or [`GPS-denied environment`](#gps-denied) and **in the absence of an exact map**
2. `Navigation in a dynamic and unknown enviroment`: robot has to **navigate in an unknown environment** where structures may have been **damaged and changed due to the disaster**
3. `Finding survivors`: robot required to **detect debris and humans under different light conditions**, deal with **[`occlusion`](#occlusion) by objects**, and **recognize deformed shapes**
4. `Communication`: robots must **communicate with rescue team outside the damaged space**. Robot may need to rely on **large databases** and the **processing power of central computers**

## <a id="tech"></a> Technologies

- In order to move around the **environment successfully**, the robot needs a **map**

- [`GPS signals`](#gps) usually used for **navigation in open spaces** since received **signals are accurate**, unlike for indoor spaces

- Hence, the design team at *BotPro* needs to create a **visual situational awareness** and are looking at **[`computer vision`](#computer-vision) techniques** to allow the robot to **produce a map of its surroundings** and **recognize objects not seen before**

- Robot must be equipped with an [`odometry sensor`](#odometry-sensor) and a single **camera** at the most basic level

### <a id="cv"></a> Computer vision
---

#### <a id="vslam"></a> Visual simultaneous localization and mapping (vSLAM)
---

#### <a id="pose-estimation"></a> Pose estimation
---

## <a id="issues"></a> Social and ethical issues

## <a id="research"></a> Further research

## <a id="challenges"></a> Challenges faced

## <a id="terms"></a> Additional terminology

- <a id="bundle-adjustment">`Bundle adjustment`</a>
- <a id="computer-vision">`Computer vision`</a>
- <a id="dead-reckoning-data">`Dead reckoning data`</a>
- <a id="edge-computing">`Edge computing`</a>
- <a id="global-map-optimization">`Global map optimization`</a>
- <a id="gps">`Global positioning system (GPS) signal`</a>
- <a id="gps-degraded">`GPS-degraded environment`</a>
- <a id="gps-denied">`GPS-denied environment`</a>
- <a id="hpe">`Human pose estimation (HPE)`</a>
- <a id="imu">`Inertial measurement unit (IMU)`</a>
- <a id="keyframe-selection">`Keyframe selection`</a>
- <a id="key-points">`Key points/pairs`</a>
- <a id="lidar">`Light detection and ranging (LIDAR)`</a>
- <a id="occlusion">`Object occlusion`</a>
- <a id="odometry-sensor">`Odometry sensor`</a>
- <a id="optimization">`Optimization`</a>
- <a id="relocalization">`Relocalization`</a>
- <a id="rpe">`Rigid pose estimation (RPE)`</a>
- <a id="robot-drift">`Robot drift`</a>
- <a id="slam">`Simultaneous localization and mapping (SLAM)`</a>
- <a id="sensor-fusion-model">`Sensor fusion model`</a>
- <a id="vslam">`Visual simultaneous localization and mapping (vSLAM) modules`:</a>
    - <a id="initialization">`Initialization`</a>
    - <a id="local-mapping">`Local mapping`</a>
    - <a id="loop-closure">`Loop closure`</a>
    - <a id="relocalization">`Relocalization`</a>
    - <a id="tracking">`Tracking`</a>


