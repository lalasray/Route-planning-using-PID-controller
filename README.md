# Controls-PID

##Overview

In this project, is necessary to build a PID controller that will handle the inputs from the Udacity's SDCE Term 2 simulator. For this, the hyperparameters for the controller should be tuned so the simulation can run as intended, with the car staying in the driveable portion of the road.

###Describe the effect each of the P, I, D components.

* **Proportional gain:** Describes the change in the output to reduce the error reported by the system. In this case, the cross-track error (CTE) that describes how far from the center of the road is the vehicle compared with the trajectory followed by the steering taken as input. The proportional gain accounts for the present values of the error, and how large will be the change to the original input. If the error is large, the change is going to be large. This value had the most direct effect in the vehicles steering, causing large corrections to the trajectory (for example, is the error indicated that the car was to far on the left of the center the road, a large correction to the right will be applied).
* **Integral gain:** This value describes the change of the output based on the cumulative sum of the past errors. This value has a subtle change, making the steering more smooth on paths were the error can be too big causing a disproportional response from the proportional gain value (like in the exit of the bridge in the simulator). This value compensates for bias in the system, that are constant errors that affect the ouput of the system. By being the cumulative sum of the all the CTE, it will grow large enough to eventually correct the output, if the proportional response is not sufficiently strong to correct it.
* **Derivative gain:** This gain takes in account the rate of change of the error, to avoid possible future trends of the error. This is represented as the tendency to overshoot and oscillate greatly trying to find the correct path. The derivative gain compensates the trend and reduces the oscillation, making the output to converge smoothly with the expected trajectory.

## Dependencies

* cmake >= 3.5
  Run
     
* uWebSockets
  Run
     sudo chmod u+x install-ubuntu.sh && ./install-ubuntu.sh
* Simulator. 
  Download it from (https://github.com/udacity/self-driving-car-sim/releases/tag/v1.45).
  unzip
  Run
      sudo chmod +x term2_sim.x86_64 && ./term2_sim.X86_64

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
4. Run it: `./pid
5. Run it:  ./term2_sim.X86_64  (in another terminal)
6. select pid controller and autonomus mode.
