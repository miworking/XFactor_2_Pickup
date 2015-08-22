# 1. Pickup
![Pickup](https://raw.githubusercontent.com/miworking/XFactor_PickupRecognition/master/app/src/main/res/mipmap-xhdpi/ic_launcher.png)

## How it works
Once the app is opened, it will go to the background immediately, so there is no UI for this app.
Then it will work in the background as a service, monitoring the user's gesture to decide whether the phone is opened by the owner or not.


## How to kill it:
 Since this app has no UI, and only works as a background service, it can only be killed manually in the settings of the system.
 
 ![Settings](https://lh4.googleusercontent.com/DGbT7aMeklh3Kn6Aj3HtO56_wCn2o7ovyYU7ZGLsUVUcNKTYjPEjhULFSYfioYmJnUsOkKmpbpMUh7U=w1000-h398-rw)
![Pickup](https://lh3.googleusercontent.com/FUaJlwOMH3q72a0aJRSn2tNsLKyhA8YvXzwsq14-ubm2TZAZO-NsmGeKkyzDb-ERfW-BFxJg8Evix-M=w1000-h398-rw)
![Kill](https://lh5.googleusercontent.com/USqPWuuFbBb-VnK4VJbg47UR4HUTKxirfc79NFk7-p0W-2bF7kmpggjR2JlyRB1bSOxTn78CIg9QDvQ=w1000-h398-rw)
## Code explanation:


##[Analysis of the result](https://www.dropbox.com/s/bnvwc62nh7kt24q/Pickup.pptx?dl=0)


##Summary:
 
1. 104 features
{Accelerometer, Magnetic} * {X,Y,Z,Magnitude} * {Mean, Std, Min, Max, Percentile25,50,75, FTT[0,1,2]}
2. data of 6 people, 547 instances
3. Cross -validation on training set: 98% correctly classified (RandomForest, 10 folders)
4. Performance on android phone: ANR android not responding....  GC_FOR_ALLOC 
 
