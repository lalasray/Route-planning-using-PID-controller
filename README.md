# Controls-PID

##Overview

In this project, is necessary to build a PID controller that will handle the inputs from the Udacity's SDCE Term 2 simulator. For this, the hyperparameters for the controller should be tuned so the simulation can run as intended, with the car staying in the driveable portion of the road.

###Describe the effect each of the P, I, D components had in your implementation.

* **Proportional gain:** Describes the change in the output to reduce the error reported by the system. In this case, the cross-track error (CTE) that describes how far from the center of the road is the vehicle compared with the trajectory followed by the steering taken as input. The proportional gain accounts for the present values of the error, and how large will be the change to the original input. If the error is large, the change is going to be large. This value had the most direct effect in the vehicles steering, causing large corrections to the trajectory (for example, is the error indicated that the car was to far on the left of the center the road, a large correction to the right will be applied).
* **Integral gain:** This value describes the change of the output based on the cumulative sum of the past errors. This value has a subtle change, making the steering more smooth on paths were the error can be too big causing a disproportional response from the proportional gain value (like in the exit of the bridge in the simulator). This value compensates for bias in the system, that are constant errors that affect the ouput of the system. By being the cumulative sum of the all the CTE, it will grow large enough to eventually correct the output, if the proportional response is not sufficiently strong to correct it.
* **Derivative gain:** This gain takes in account the rate of change of the error, to avoid possible future trends of the error. This is represented as the tendency to overshoot and oscillate greatly trying to find the correct path. The derivative gain compensates the trend and reduces the oscillation, making the output to converge smoothly with the expected trajectory.

## Dependencies

* cmake >= 3.5
 * All OSes: [click here for installation instructions](https://cmake.org/install/)
* make >= 4.1
  * Linux: make is installed by default on most Linux distros
  * Mac: [install Xcode command line tools to get make](https://developer.apple.com/xcode/features/)
  * Windows: [Click here for installation instructions](http://gnuwin32.sourceforge.net/packages/make.htm)
* gcc/g++ >= 5.4
  * Linux: gcc / g++ is installed by default on most Linux distros
  * Mac: same deal as make - [install Xcode command line tools]((https://developer.apple.com/xcode/features/)
  * Windows: recommend using [MinGW](http://www.mingw.org/)
* [uWebSockets](https://github.com/uWebSockets/uWebSockets)
  * Run either `./install-mac.sh` or `./install-ubuntu.sh`.
  * If you install from source, checkout to commit `e94b6e1`, i.e.
    ```
    git clone https://github.com/uWebSockets/uWebSockets 
    cd uWebSockets
    git checkout e94b6e1
    ```
    Some function signatures have changed in v0.14.x. See [this PR](https://github.com/udacity/CarND-MPC-Project/pull/3) for more details.
* Simulator. You can download these from the [project intro page](https://github.com/udacity/self-driving-car-sim/releases) in the classroom.

There's an experimental patch for windows in this [PR](https://github.com/udacity/CarND-PID-Control-Project/pull/3)

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid`. 
