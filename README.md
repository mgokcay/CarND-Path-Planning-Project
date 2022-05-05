# CarND-Path-Planning-Project
Self-Driving Car Engineer Nanodegree Program
### Goals
In this project your goal is to safely navigate around a virtual highway with other traffic that is driving +-10 MPH of the 50 MPH speed limit. You will be provided the car's localization and sensor fusion data, there is also a sparse map list of waypoints around the highway. The car should try to go as close as possible to the 50 MPH speed limit, which means passing slower traffic when possible, note that other cars will try to change lanes too. The car should avoid hitting other cars at all cost as well as driving inside of the marked road lanes at all times, unless going from one lane to another. The car should be able to make one complete loop around the 6946m highway. Since the car is trying to go 50 MPH, it should take a little over 5 minutes to complete 1 loop. Also the car should not experience total acceleration over 10 m/s^2 and jerk that is greater than 10 m/s^3.

### Prediction main.cpp:107-143
In this step, sensor fusion data is analyzed if the current and adjecent lanes are free or occupied. 
Car's lanes are determined according to d values at Frenet frame. (main.cpp:115-121)
Since the sensor fusion data is delayed, and we are calculating a path acutually for future; car's positions for the time that the path will be calculated, are predicted using their speed. (main.cpp:131)


### Behaviour
Once the lane's status (free, occupied) is determined a behaviour is selected to keep current lane or change to left/right lane. If there is a slow car ahead and lane change is not possible than the speed of the card decrased. (main.cpp:148-168)

Than a path is calculated with the remaining points from the previous path and adding three new way points 30m in between.
All points are transfered to local car coordinates. (main.cpp:218-224)

Than spline library is used to generate path between these waypoints. To adjust the vehicle's speed number of points taken from the spline is determined according to calculated speed. (main.cpp:252-254)
