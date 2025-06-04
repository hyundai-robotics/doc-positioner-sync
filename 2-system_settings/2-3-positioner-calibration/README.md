# 2.3 Positioner Calibration

- Positioner calibration is a function that automatically calculates the position and movement direction of the positioner using the robot’s TCP pose. Therefore, to obtain accurate results from positioner calibration, the robot’s TCP pose must be input precisely. As a preliminary step, the “[System > 6: Auto Calibration > Optimize axis origin and tool length]” function can be utilized.

- To use positioner calibration, a group number must be assigned to the positioner axis. A positioner group can consist of up to 2-axes, which can be configured as either rotary-rotary or linear-linear.

- The basic principle of positioner calibration is that, for positioners composed of rotary axes, the positions of three taught points are used to form a circle to calculate the position of the rotation axis.
  Therefore, three taught points per axis are required to calculate the center of each rotary axis.
  In the case of a two-axis positioner with rotary axes, a common middle point is used, totaling five taught points, to calculate the position and direction of each rotation axis.
  For positioners composed of linear axes, since only the axis direction is calculated, two taught points per axis are required.
  For a two-axis linear positioner, the middle point is shared, and the direction of each axis is calculated from three taught points.

- After program teaching, positioner calibration can be performed from the settings screen or by executing the ```posi_calib``` procedure.
