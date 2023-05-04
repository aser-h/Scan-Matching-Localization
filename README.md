# Scan-Matching-Localization
 ## Localization project from Udacity's self driving car nano-degree
##  Project Overview
In this project the goal will be to localize a car driving in simulation for at least 170m from the starting position and never exceeding a distance pose error of 1.2m. The simulation car is equipped with a lidar, provided by the simulator at regular intervals are lidar scans. There is also a point cloud map `map.pcd` already available, and by using point registration matching between the map and scans localization for the car can be accomplished. This point cloud map has been extracted from the CARLA simulator.
___
## Controlling the car
### Throttle ( UP Key )
Each tap will increase the throttle power. Three presses is a good amount of throttle power.
### Reverse/Stop ( Down Key )
A single tap will stop the car and reset the throttle to zero if it is moving. If the car is not moving it will apply throttle in the reverse direction.

### Steer ( Left/Right Keys )
Tap these keys to incrementally change the steer angle. The green line extruding out in front of the red box in the image above represents the steer value and its end point will move left/right depending on the current value.

### Center Camera ( a )
### Press this key to recenter the camera with a top down view of the car.

### Rotate Camera ( mouse left click and drag )
### Pan Camera ( mouse middle button and drag)
### Zoom (mouse scroll)
___
## To get started do the following steps:
### 1. Compile the code (Terminal Tab 1)
    cd /home/workspace/c3-project
    cmake .
    make
### 2. Launch the simulator in a new terminal tab (Terminal Tab 2)
    su - student

    cd /home/workspace

    ./run-carla.sh

### 3. Run the project code back in the first tab (Terminal Tab 1)
    cd /home/workspace/

    ./cloud_loc
___    
## Project Steps
All of the work for the project can be found within `c3-main.cpp` .

### Step 1: Filter scan using voxel filter

### Step 2: Find pose transform by using ICP or NDT matching

ICP matching was implemented in this project.

### Step 3: Transform the scan so it aligns with ego's actual pose and render that scan
___
In this project, the chosen algorithm for aligning point clouds is 3D ICP algorithm. The voxel filter is used to reduce the number of points in the point clouds and it has a parameter called ‘filterRes’ that determines the size of the voxels. The ‘filterRes’ value is set to ‘0.5’ in this project. The number of iterations is another parameter that affects the accuracy and speed of the algorithm. The number of iterations is set to ‘4’ in this project. The scan that is transformed by the algorithm is named ‘newscanCloud’. The video that follows demonstrates the result of implementing these steps on a car that drives autonomously. The car was able to drive a distance of 170 meters without exceeding a pose error of 1.2 meters.

### Localization Video
![Alt text](imgs%20&%20vids/the%20localization.gif)

### Screenshot after the car finished the 170m journey.
![Alt text](imgs%20&%20vids/Screenshot%20after%20170m%20journey.png)