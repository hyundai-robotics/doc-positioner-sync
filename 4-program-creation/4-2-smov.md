# 4.2 smov

```py
	smov {station number}, {interpolation method}, {speed}, {accuracy}, {tool number}
```

- The settings of the smov command are determined within the positioner coordinate system.
  For example, when moving two points in a straight line with the positioner moving, the speed refers to the TCP's movement speed relative to the positioner.

1. Station number: Refers to the positioner group number (S1 ~ S4).
2. Interpolation method: Linear(L) or circular(C) interpolation can be performed on the workpiece.
3. Speed: Sets the speed at which the robot’s TCP moves over the workpiece.
4. Accuracy: Sets the accuracy for linear and circular interpolation over the workpiece.
5. Tool number: Sets the robot tool number used for the operation.
