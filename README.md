# UD_CarND_PID_Control_Project
Udactiy Self Driving Car Nanodegree - PID Contorl Project

## Driving a Vehicle with PID Control

### Results
A video of the simulated car driving around the track can be found [here](Video.mp4)

### PID controller
* The "P" for proportional means that the car will steer in proportion to the cross-track error, or CTE. CTE is essentially how far from the middle line of the road the car is. This makes sense, as if the car is to the left of the line then you would want to steer to the right; if it is far to the left of the middle with a high CTE then you want a higher steering angle. However, if the coefficient is set too high for P, the car will oscillate a ton, as the car will constantly overcorrect and overshoot the middle. If the coefficient is too low, the car may react too slowly to curves when the car gets off-center with a higher CTE.
* The "I" for integral sums up all CTEs up to that point, such that too many negative CTEs (in this case, meaning the car has been to the left of the middle of the lane for awhile) will drive up this value, causing the car to turn back toward the middle, preventing the car from driving on one side of the lane the whole time. If the coefficient is too high for I, the car tends to have quicker oscillations, and does not tend to get up to a quick speed. A low coefficent for I will cause the car to tend to drift to one side of the lane or the other for longer periods of time.
* The "D" for derivate is the change in CTE from one value to the next. This means that 1) if the derivative is quickly changing, the car will correct itself (i.e. higher steering angle) faster, such as in the case of a curve, and 2) if the car is moving outward from the middle, this will cause the steering to get larger (as the derivative sign will match the proportional sign), but if the car is moving toward the center (meaning the derivative value will be negative), the car's steering angle will get smoothed out, leading to a more smoother driving experience. Too high of a coefficient leads to almost constant steering angle changes of large degrees, where although the car will be well-centered it can hardly move. Too low of a D coefficient will lead to the oscillations being too high with more overshooting.

### PID coefficients
I had used Twiddle at the beginning to try out some start coefficients but i removed the Twiddle function from the final code as it is not required anymore. After some tests with different coefficients i came to the conclusion, that the values from the original project lessons work really sufficient. I decided not to use Twiddle for the fine tuning as it tended to vary greatly.

In the end, the final values were determined by manual tuning and driving several runs around the track. I also tried lowering and raising my coefficients in conjunction to each other as well as tuning each individually. Most of the time i was creating too high steering angles which ended up in some really unsmooth driving. Whenever the values got too low the car had problems with larger curves and struggled to finish the round.
