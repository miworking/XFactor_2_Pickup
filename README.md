# 1. App Name: Pickup 
![Pickup](https://raw.githubusercontent.com/miworking/XFactor_PickupRecognition/master/app/src/main/res/mipmap-xhdpi/ic_launcher.png)

## What does it do:
Once the app is opened, it will go to the background immediately, so there is no UI for this app.
Then it will work in the background as a service, monitoring the user's gesture to decide whether the phone is opened by the owner or not.


## How to kill it:
 Since this app has no UI, and only works as a background service, it can only be killed manually in the settings of the system.
 
 ![Settings](https://lh4.googleusercontent.com/DGbT7aMeklh3Kn6Aj3HtO56_wCn2o7ovyYU7ZGLsUVUcNKTYjPEjhULFSYfioYmJnUsOkKmpbpMUh7U=w1000-h398-rw)
![Pickup](https://lh3.googleusercontent.com/FUaJlwOMH3q72a0aJRSn2tNsLKyhA8YvXzwsq14-ubm2TZAZO-NsmGeKkyzDb-ERfW-BFxJg8Evix-M=w1000-h398-rw)
![Kill](https://lh5.googleusercontent.com/USqPWuuFbBb-VnK4VJbg47UR4HUTKxirfc79NFk7-p0W-2bF7kmpggjR2JlyRB1bSOxTn78CIg9QDvQ=w1000-h398-rw)

## How it works
When the screen is turned off, all sensor data will be collected by this service automatically, and these data will be written into a local csv file in external folder like this: /storage/emulated/legacy/Android/data/edu.cmu.ebiz.pickup/files/

Only accelerometer and magnetic sensor data will be used, so there will be two files in this folder: 2015_08_21_23_47_55_acc.csv and 2015_08_21_23_47_55_magetic.csv (Why other sensor data are not used? [Page 2](https://www.dropbox.com/s/bnvwc62nh7kt24q/Pickup.pptx?dl=0) )



##[Analysis of the result](https://www.dropbox.com/s/bnvwc62nh7kt24q/Pickup.pptx?dl=0)


##Summary:
 
1. 104 features
{Accelerometer, Magnetic} * {X,Y,Z,Magnitude} * {Mean, Std, Min, Max, Percentile25,50,75, FTT[0,1,2]}
2. data of 6 people, 547 instances
3. Cross -validation on training set: 98% correctly classified (RandomForest, 10 folders)
4. Performance on android phone: ANR android not responding....  GC_FOR_ALLOC 
 
