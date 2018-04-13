
PROJECT DESCRIPTION
The project "unscented Kalman filter" is based on the same structure as the extended Kalman filter.
It uses a main file that calls a function called ProcessMeasurement. Anything important happens in this function. The function is part of the class ukf.



ALGORITHM


ukf.cpp file consists of 5 methods :

1. Initialization
2. Process Measurement 
3. Prediction
4. UpdateLidar
5. UpdateRadar

Intialization:

This is all about initializing the Unscented Kalman Filter variables  . I have modified the 
logitudnal and yaw rate acceleration noise along with some other required variables that are need in UKF.
I have untouched the Radar Noise noise variables as they are provided by the manufacture and for this project it is already provided.

Process Measurement:

This method is  used to determine the source of measurement data that can be either lidar or radar only and then call the Prediction followed by the Update method of the respective sensor. Once the source of data is checked I have initialized the state vector and the covariance vector and then initial measurement are set based upon the sensor type.

For Lidar data the raw_measurement taken from the simulator are taken directly:
while For Radar data the raw measurement are transformed using the following data

Once we have the measurement we call the Prediction step followed by the Update step depending upon the sensor type.

3. Prediction

Prediction step does not depends upon the sensor type so irrespective of the sensor type prediction method will remain same.

This method include the following 4 steps whoes implementation can be found in ukf.cpp
3.1 Generate Sigma Points
3.2 Generate Augmented Sigma Points
3.3 Predict Sigma Points
3.4 Predict Mean and Covariance

4. UpdateLidar

This method uses the lidar data to update the belief about the objects position. This is done by first predicting the measurement then updating using Unscented Kalman Filter 

5. UpdateRadar

This method uses the radr data to update the belief about the objects position. This is done by first predicting the measurement then updating using Unscented Kalman Filter 

For predicting the measurement following steps are performed:

5.1 Transform sigma points into measurement space 
5.2 Predict mean measurement 
5.3 Measure the covariance matrix

For Updation Using UKF following steps are performed:
1. Calculate the cross correlation Matrix
2. Calculate the Kalman Gain
3. Update State 
4. Update Covariance Matrix


Content of this repo

`scr` a directory with the project code:
`main.cpp` - reads in data, calls a function to run the Kalman filter, calls a function to calculate RMSE
`ukf.cpp` - the UKF filter itself, defines the predict function, the update function for lidar, and the update function for radar
`tools.cpp` - a function to calculate RMSE data a directory with two input files, provided by Udacity results a directory with output files

Result


Dependencies
cmake >= v3.5
make >= v4.1
gcc/g++ >= v5.4
How to run the code
Clone this repo and perform

mkdir build && cd build
cmake .. && make
./UnscentedKF







