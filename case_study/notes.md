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
    - Designed to help with the search and rescue of humans after a **disaster** (earthquakes and tsunamis)
    - Assist the efforts of rescue teams by **searching** and **mapping** areas, assessing damage, removing debris, delivering supplies, and evacuating casualties

- Found to perform below expectations when sent into a large factory after a fire and another factory that was damaged by an earthquake

- Robot had trouble **navigating the factories** and **reaching the exact location of survivors**

- However, operation was successful when deployed in a stadium after strucutural damage

- Root cause was the accuracy and difference  of the [*`global positioning system (GPS) signal`*](#gps) inside the factories
    - Strength of the satellite signal received was **insufficient**, resulting in errors in calculating robot's exact location
    - Factories were also an **unknown environement** to the robot
    - Damage caused meant that the **layout of the factories was different to any floor plans that existed**

## <a id="problems"></a> Problems to be addressed

- Redesgining of robot with the capability to **explore**, **map**, and **survey the interior of unknown and damaged buildings**

- Must be **cost effective** and focus on the new design was on **building efficient algorithms** to **improve robot performance** and not on the mechanical components

1. `Accurate mapping of the area`: robot needs to find its way inside buildings and reliably operate in a [*`GPS-degraded environment`*](#gps-degraded) or [*`GPS-denied environment`*](#gps-denied) and **in the absence of an exact map**
2. `Navigation in a dynamic and unknown enviroment`: robot has to **navigate in an unknown environment** where structures may have been **damaged and changed due to the disaster**
3. `Finding survivors`: robot required to **detect debris and humans under different light conditions**, deal with **[`occlusion`](#occlusion) by objects**, and **recognize deformed shapes**
4. `Communication`: robots must **communicate with rescue team outside the damaged space**. Robot may need to rely on **large databases** and the **processing power of central computers**

## <a id="tech"></a> Technologies

- In order to move around the **environment successfully**, the robot needs a **map**

- [`GPS signals`](#gps) usually used for **navigation in open spaces** since received **signals are accurate**, unlike for indoor spaces

- Hence, the design team at *BotPro* needs to create a **visual situational awareness** and are looking at **[*`computer vision`*](#computer-vision) techniques** to allow the robot to **produce a map of its surroundings** and **recognize objects not seen before**

- Robot must be equipped with an [*`odometry sensor`*](#odometry-sensor) and a single **camera** at the most basic level

### <a id="cv"></a> Computer vision
---

- Refers to technologies that allow a device to **"see"**, i.e., **sense the environment around it**, including both **static** and **dynamic objects**

- Two subdomains of [`computer vision`](#computer-vision) being explored include:
    - [*`Visual simultaneous localization and mapping (vSLAM)`*](#vslam)
    - [`Pose estimation`](#pose-estimation)

#### <a id="vslam"></a> Visual simultaneous localization and mapping (vSLAM)
---

> [*`Simultaneous localization and mapping (SLAM)`*](#slam) is used for estimating sensor motion and reconstructing the structure of an unknown environment

- [`SLAM`](#slam) can be performed using different types of **sensors** including:
    - cameras for **visual data** collection
    - radar
    - sonar
    - [*`light detection and ranging (LIDAR)`*](#lidar) for **non-visible data**
    - [*`inertial measurement unit (IMU)`*](#imu) for **basic positional data**

> [`IMU`](#imu) is a combination of sensors, such as an `accelerometer`, `gyroscope`, and `magnetometer`, that capture the data about a device's location in a three-dimensional (3D) space

- Installing an [`IMU`](#imu) on the robot will allow it to measure its **translational and rotational movements**

> [`SLAM`](#slam) techniques that use a camera as the basic visual input are know as [`vSLAM`](#visual-slam) or [`visual SLAM`](#visual-slam)

- [`vSLAM`](#visual-slam) algorithms will allow the robot to **dynamically build a map** while **keeping track of its own location and orientation** as it moves around an **unknown environment**

- The objective is to **combine** the [*`dead reckoning data`*](#dead-reckoning-data) provided by the [`odometry sensor`](#odometry-sensor) and **images from the camera** as an **input** to undertake `localization` and **map building**

- [`vSLAM`](#visual-slam) works indoor and provides greater accuracy than [`GPS`](#gps) (advantage)

![vSLAM process chart](./img/fig1.png)

- [`vSLAM`](#visual-slam) algorithm has a number of **modules**, the *three* main ones being:
    - [*`tracking`*](#tracking)
    - [*`local mapping`*](#local-mapping)
    - [*`loop closure`*](#loop-closure)

![The three main modules of the vSLAM algorithm](./img/fig2.png)

- Robot uses the ***three* main modules** of the [`vSLAM`](#visual-slam) algorithm to:
    - [`initialize`](#initialization) its position according to the available data
    - [`track`](#tracking) its progress while analyzing new sensor data
    - **create a map** of the environment

- As the measurement of features (doors, wall corners, location/pose of people in damaged structure) *increases* over time, the **environment representation** needs to be **optimized**, which requires significant **computational processing capabilites** (**Figure 3**)

- **Balance** is needed between the `efficiency of the optimizing algorithms` and the `accuracy of the created map`

- Two techniques used for [*`optimization`*](#optimization) are [*`bundle adjustment`*](#bundle-adjustment) and [*`keyframe selection`*](#keyframe-selection)

<p align="center"><img src="./img/fig3.png" width="50%" alt="Flowchart of a typical vSLAM process"></p>

- When [`tracking`](#tracking) fails, [`vSLAM`](#visual-slam) executes a model for [*`relocalization`*](#relocalization) since the robot needs to **relocalize** itself

- As the robot moves through a space, it may [`drift`](#robot-drift) and **lose itself** at which point [*`global map optimization`*](#global-map-optimization) (using a [`loop closure`](#loop-closure) technique) is executed

- [`vSLAM`](#visual-slam) is a **low-cost** and **robust** algorithm that can handle **dynamic changes in the environment**

- Need to know the **performance**, **advantages**, and **limitations** of the [`vSLAM`](#visual-slam) algorithm

- Design team are also exploring using **multiple cameras** in the new robot

- If implemented, a **different image acquisition scheme** may be used to **optimize the use of visual information**

#### <a id="pose-estimation"></a> Pose estimation
---

- Robot needs to know the **pose of a person** to perform **correct operations** and needs to **estimate the configuration of human body parts**

> [`Pose estimation`](#pose-estimation) refers to the [`computer vision`](#computer-vision) technologies of estimating the position and orientation of an object or a human relative to the camera in a real-world space

- Usually done by **identifying**, **locating**, and **tracking** a number of [*`key points`*](#key-points) on an **object** or a **human** in an **interactive environment**

> [`Key points`](#key-points) are spatial locations or points in an image that define what stands out in the image captured

- Inanimate objects are **rigid**, so their [`key points`](#key-points) include **corners**, **edges**, or other significant features

> Models used to identify [`key points`](#key-points) on inanimate objects are called [*`rigid pose estimation (RPE)`*](#rpe) models

- [`Key points`](#key-points) for humans include the **head** and other **major joints** such as the neck, shoulders, elbows, wrists, and knees

> Models used to identify [`key points`](#key-points) on humans are called [*`human pose estimation (HPE)`*](#hpe) models

<p align="center"><img src="./img/fig4.png" width="50%" alt="A kinematic representation of a human body"></p>

- [`Key points`](#key-points) used to describe **pose of human** in **two dimensions**

> A valid connection between points is known as a [`pair`](#key-points)

- This `two-dimensional (2D)` image of [`key points`](#key-points) and [`pairs`](#key-points) is transformed into a **3D pose model** that enables the **prediction of the accurate positioning** of a person

> **Note**: [`HPE`](#hpe) does not recognize who is in the image; it only **estimates the body parts**

![3D human pose estimation](./img/fig5.png)

- [`HPE`](#hpe) classified into:
    - `Bottom-up` methods
    - `Top-down` methods

- [`HPE`](#hpe) methods differ based on **number of people being tracked**

- `Single-person pose estimation` easier than `multiple-person pose estimation`

- Robot with highly **accurate** image of people:
    - Increase in `computational complexity` &rarr; Increase in `inference delay` in **real-time rescue operations**

- **Challenges** faced by `pose-tracking` algorithms:
    - **Background scene handling**
    - [`Self-occlusion`](#occlusion) of **body parts**
    - `Tracking` in **diverse light conditions**
    - [*`Multiple-object occlusion`*](#occlusion)

- Robots must undertake `pose estimation` in **real time**, with or without **internet connectivity**, so the design team might consider using **lightweight edge devices** that implement [*`edge computing`*](#edge-computing)

- Challenging for robots to work with **low-power devices**

- Robot also needs `two-way communication` with the **human rescue team**

- Design team aware that **access to data/images** sent by the rescue robot should be **limited to authorized persons** to maintain the **security and privacy of data**

## <a id="issues"></a> Social and ethical issues

- Advantages:
    - Sent to places that are too **dangerous for human rescue workers**
    - Designed to assist humans, saving human rescue workers from **exhaustion and trauma**
    - Robots can **gather feedback** from **mock deployments** that can be used to **train human rescue workers** about **safety and efficiency** in disaster management teams

- However, robots **require large amounts of resources to build and maintain**, yet they may have **limited capability**

- Hence, only **economically developed countries** can **afford to spend time and money** on building and using them

- **Questions** regarding **social and ethical aspects** of using rescue robots:

    > Should rescue robots be used to perform tasks that would be too dangerous for humans in a disaster or similarly unstable environment?

    > Are robots safe? Who is accountable if a rescue robot causes harm to the person in need of help due to a miscalculation of the person's pose?

    > Will survivors be comfortble being helped by a robot and not another compassionate human being?

## <a id="research"></a> Further research

- [*`Sensor fusion models`*](#sensor-fusion-model) can be used in the future to provide **greater confidence and accuracy**

- Making **multiple robots** that can work **collaboratively** will require the company to identify the **algorithms** that can be used to enable **collaboration** not just **between robots** but also with their **human operators**

- Technologies like `intelligent network infrastructure` that can be **dynamically enhanced and extended** by `edge nodes` could serve as the **backbone**

- The ability to be **connected in any place and at any time** would allow a necessary **level of autonomy** and **collective exchange of information** among robots, humans, infrastructure and related applications

- However, this could require more **advanced [`edge computing`](#edge-computing)** and **distributed `machine learning`**

- Building a rescuer `graphical user interface (GUI)` that could **map a disaster zone** in **real time** to prepare the human rescue team if they wanted to enter the zone

## <a id="challenges"></a> Challenges faced

> Understanding how vSLAM navigates an environment with unknown obstacles and contours

> Minimizing the time rescue robots spend scanning and learning an environment

> Estimating the pose of people despite varying light and environment conditions and body-part or multiple-object occlusion

> Updaing existing maps in a dynamically changing environment, such as an earthquake where rubble is still shifting

> Developing an understanding of the ethical considerations of using autonomous robots in life-and-death situations

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
- <a id="visual-slam">`Visual simultaneous localization and mapping (vSLAM) modules`:</a>
    - <a id="initialization">`Initialization`</a>
    - <a id="local-mapping">`Local mapping`</a>
    - <a id="loop-closure">`Loop closure`</a>
    - <a id="relocalization">`Relocalization`</a>
    - <a id="tracking">`Tracking`</a>


