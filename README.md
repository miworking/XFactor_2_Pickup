# Pickup Pattern Recognition

## How it works
Once the app is opened, it will go to the background immediately, so there is no UI for this app.
Then it will work in the background as a service, monitoring the user's gesture to decide whether the phone is opened by the owner or not. It can only be killed manually in the settings of the system.

## 

##[Analysis of the result](https://www.dropbox.com/s/bnvwc62nh7kt24q/Pickup.pptx?dl=0)


##Summary:
 
1. 104 features
{Accelerometer, Magnetic} * {X,Y,Z,Magnitude} * {Mean, Std, Min, Max, Percentile25,50,75, FTT[0,1,2]}
2. data of 6 people, 547 instances
3. Cross -validation on training set: 98% correctly classified (RandomForest, 10 folders)
4. Performance on android phone: ANR android not responding....  GC_FOR_ALLOC 
 
