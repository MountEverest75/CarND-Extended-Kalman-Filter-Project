# Self-Driving Car Engineer Nanodegree Program
## Extended Kalman Filter Project

---

## Dependencies

[//]: # (Image References)
[image1]: ./data/ScatterPlotForSampleFile-1.png
[image2]: ./data/ScatterPlotForSampleFile-2.png
[image3]: ./data/ScatterPlotForSampleFile-3.png
[image4]: ./data/ScatterPlotForSampleFile-4.png

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

## Basic Build Instructions

1. Clone this repo.
2. Make a build directory: `mkdir build && cd build`
3. Compile: `cmake .. && make`
   * On windows, you may need to run: `cmake .. -G "Unix Makefiles" && make`
4. Run it: `./ExtendedKF path/to/input.txt path/to/output.txt`. You can find
   some sample inputs in 'data/'.
    - eg. `./ExtendedKF ../data/sample-laser-radar-measurement-data-1.txt output.txt`

## Editor Settings

We've purposefully kept editor configuration files out of this repo in order to
keep it as simple and environment agnostic as possible. However, we recommend
using the following settings:

* Indent using spaces
* Set tab width to 2 spaces (keeps the matrices in source code aligned)

## Code Style

Please (do your best to) stick to [Google's C++ style guide](https://google.github.io/styleguide/cppguide.html).

## Generating Additional Data

This is optional!

If you'd like to generate your own radar and lidar data, see the
[utilities repo](https://github.com/udacity/CarND-Mercedes-SF-Utilities) for
Matlab scripts that can generate additional data.

## Project Instructions and Rubric

Note: regardless of the changes you make, your project must be buildable using
cmake and make!

More information is only accessible by people who are already enrolled in Term 2
of CarND. If you are enrolled, see [the project page](https://classroom.udacity.com/nanodegrees/nd013/parts/40f38239-66b6-46ec-ae68-03afd8a601c8/modules/0949fca6-b379-42af-a919-ee50aa304e6a/lessons/f758c44c-5e40-4e01-93b5-1a82aa4e044f/concepts/12dd29d8-2755-4b1b-8e03-e8f16796bea8)
for instructions and the project rubric.

## Results
The following results have been observed after executing two tests detailed below on Extended Kalman filter.
#### 1. RMSE results after running with "sample-laser-radar-measurement-data-1.txt" can be found below:

Input: `sample-laser-radar-measurement-data-1.txt`

Process:
`./ExtendedKF ../data/sample-laser-radar-measurement-data-1.txt ../data/output-1.txt`

Command executed after noise adjustments.

`./ExtendedKF ../data/sample-laser-radar-measurement-data-1.txt ../data/output-noiseadj-1.txt`

Output Files: `output-1.txt` and `output-noiseadj-1.txt`

Results:

Before noise adjustment:
```
Accuracy - RMSE:
0.0651648
0.0605379
 0.533212
 0.544193
```

After noise adjustment:
```
Accuracy - RMSE:
0.0388008
0.0366848
  0.41763
 0.461049
 ```

#### 2. RMSE results after running with "sample-laser-radar-measurement-data-2.txt" can be found below:

Input: ```sample-laser-radar-measurement-data-2.txt```

Process: ```./ExtendedKF ../data/sample-laser-radar-measurement-data-2.txt ../data/output-2.txt```

Command executed after noise adjustments.

`./ExtendedKF ../data/sample-laser-radar-measurement-data-2.txt ../data/output-noiseadj-2.txt`

Output File: ```output-2.txt``` and ```output-noiseadj-2.txt```

Results:

```
Accuracy - RMSE:
0.185476
0.190359
0.487633
0.816566
```

After noise adjustment:
```
Accuracy - RMSE:
0.186544
0.191394
0.540929
 1.13263
```

Examining the results above indicates that the RMSE values generated are within the acceptable range.

## Analysis
Performing trace and scatter of results shows that for first sample file there are some outliers by observing the blue lines at the left bottom of the eight shape trace.

![alt text][image1]

This indicates that estimates done by Extended Kalman Filter program are slightly off, however it could be inferred from the graphs that they are closer to actual measurements.

The results from the second sample file show less outliers while comparing EKF estimates with ground truth.
![alt text][image2]

Although the results are satisfactory testing this approach with more data is desirable to fine tune any deviations.

It has been observed that changing the noise parameters from 9 to 30 improved the results for first sample dataset. The revised scatter plot has been showcased below:

![alt text][image3]

However the EKF process did not show any improvement in estimates using second dataset.

![alt text][image4]

The details of scatter plot can be found in the iPython notebook ekf-visualization.ipynb.
