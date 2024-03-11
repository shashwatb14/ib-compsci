# Rescue Robots

## Important links:
- [Actual case study](./rescue_robots.pdf)
- [Computer Science wiki for vocabulary](https://computersciencewiki.org/index.php?title=2024_case_study)

## Scenario

- **BotPro**:
    - Company that makes robots for various industrial applications
    - Focus shifted to making **rescue robots**

- **Rescue robots**:
    - Designed to help with the search and rescue of humans after a **disaster** (like earthquakes and tsunamis)
    - Assist the efforts of rescue teams by **searching** and **mapping** areas, assessing damage, removing debris, delivering supplies, and evacuating casualties

- Found to perform below expectations when sent into a large factory after a fire and another factory that was damaged by an earthquake

- Robot had trouble **navigating the factories** and **reaching the exact location of survivors**

- However, operation was successful when deployed in a stadium after strucutural damage

- Root cause was the accuracy and difference  of the `global positioning system (GPS) signal` inside the factories
    - Strength of the satellite signal received was **insufficient**, resulting in errors in calculating robot's exact location
    - Factories were also an **unknown environement** to the robot
    - Damage caused meant that the **layout of the factories was different to any floor plans that existed**

## Problems to be addressed

- Redesgining of robot with the capability to **explore**, **map**, and **survey the interior of unknown and damaged buildings**

- Must be **cost effective** and focus on the new design was on **building efficient algorithms** to **improve robot performance** and not on the mechanical components

1. `Accurate mapping of the area`: robot needs to find its way inside buildings and reliably operate in a `GPS-degraded environment` or `GPS-denied environment` and **in the absence of an exact map**
2. `Navigation in a dynamic and unknown enviroment`: robot has to **navigate in an unknown environment** where structures may have been **damaged and changed due to the disaster**
3. `Finding survivors`: robot required to **detect debris and humans under different light conditions**, deal with **`occlusion` by objects**, and **recognize deformed shapes**
4. `Communication`: robots must **communicate with rescue team outside the damaged space**. Robot may need to rely on **large databases** and the **processing power of central computers**

## Technologies

## Computer vision

## Visual simultaneous localization and mapping (vSLAM)

## Pose estimation

## Social and ethical issues

## Further research

## Challenges faced

## Additional terminology

- `Bundle adjustment`
- `Computer vision`
- `Dead reckoning data`
- `Edge computing`
- `Global map optimization`
- `Global positioning system (GPS) signal`
- `GPS-degraded environment`
- `GPS-denied environment`
- `Human pose estimation (HPE)`
- `Inertial measurement unit (IMU)`
- `Keyframe selection`
- `Key points/pairs`
- `Light detection and ranging (LIDAR)`
- `Object occlusion`
- `Odometry sensor`
- `Optimization`
- `Relocalization`
- `Rigid pose estimation (RPE)`
- `Robot drift`
- `Simultaneous localization and mapping (SLAM)`
- `Sensor fusion model`
- `Visual simultaneous localization and mapping (vSLAM) modules`:
    - `Initilization`
    - `Local mapping`
    - `Loop closure`
    - `Relocalization`
    - `Tracking`


