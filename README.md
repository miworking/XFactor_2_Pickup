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

Once the screen is turned on, it will read these data from local files, and abstract features from them, and decide whether it is the owner that picked up this phone. Decison is made basing on a random forest model which was trained before, this model file is located in [assets](https://github.com/miworking/XFactor_PickupRecognition/tree/master/app/src/main/assets) folder. And we are using Random Forest algorithm prived by [Weka](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CB8QFjAAahUKEwjusbKs5bvHAhXKez4KHb80D3M&url=http%3A%2F%2Fwww.cs.waikato.ac.nz%2Fml%2Fweka%2F&ei=VvLXVe6uL8r3-QG_6byYBw&usg=AFQjCNEPpma7O48lI77yyDpwoLXe7vLqHQ&sig2=nmy5t8rpWRtkwt_DOQBD9g&cad=rjt), to use Weka in this app, a [weka.jar](https://github.com/miworking/XFactor_PickupRecognition/blob/master/app/libs/weka.jar) is imported, and this line needs to be added to dependencies in [build.gradle](https://github.com/miworking/XFactor_PickupRecognition/blob/master/app/build.gradle#L27)

`compile files('libs/weka.jar')`



##[Analysis of the result](https://www.dropbox.com/s/bnvwc62nh7kt24q/Pickup.pptx?dl=0)


##Summary:
 
1. 104 features
{Accelerometer, Magnetic} * {X,Y,Z,Magnitude} * {Mean, Std, Min, Max, Percentile25,50,75, FTT[0,1,2]}
2. data of 6 people, 547 instances
3. Cross -validation on training set: 98% correctly classified (RandomForest, 10 folders)
4. Performance on android phone: ANR android not responding....  GC_FOR_ALLOC 
 
