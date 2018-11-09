# CarND-Controls-MPC
Self-Driving Car Engineer Nanodegree Program

---

The Model
The vehicle model takes into account the coordinates x and y, the heading psi and the velocity v. The actuators controlling the vehicle are steering angle and throttle. Steering angle is a value between -25 and 25 and the throttle falls within [-1, 1]. Two errors are defined, the deviation from the center (cte) and the deviation from the heading (epsi). To update the values of the prediction for each step, each parameter at step t+1 is calculated based on the state of the vehicle at the current step t.

The cost of the predictions are evaluated to enable the vehicle to drive as smoothly and quickly as possible.

Timestep Length and Elapsed Duration (N & dt)
I've tried a number of timesteps and durations. If N * dt is too low (less than 0.5 second), the vehicle would overcompensate cte at low speeds and oscillate about the cte to instability. If N * dt is too high, the curve would deviate from the road as the prediction period is too long at high speeds and would cause the vehicle to "miss" the turn. Furthermore, if N is too high, the computational cost of each update would cause a lag that makes the car unstable. Also, if N is too low, the MPC curve becomes too volatile for the car to follow. If dt is too long, the actuation steps would become too slow for the vehicle to use. Also, if dt is too short, the model would try to overcompensate again at low velocities and stop the car from reaching stable speeds.


Model Predictive Control with Latency
In a real world, the execution of command does need some time, although it is a rather short period. PID is not able to solve this lantency, while MPC can do a great job. I set 100ms as the realistic latency.


