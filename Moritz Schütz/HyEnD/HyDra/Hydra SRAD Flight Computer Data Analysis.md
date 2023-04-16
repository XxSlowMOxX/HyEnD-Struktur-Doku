
#Hydra #HyEnD #Avionik
The COTS Eggtimer determined a maximum altitude of ~127m. Our SRAD Computer determined Apogee at ~80m. This difference is above the usual measuring noise of the used GPS System, and should therefore be analysed. Velocity and Acceleration Estimates will also be made.
# Barometer Analysis:
The Barometer data is smoothed, and then the first and second derivative are taken.
This should have lead to more accurate Velocity and Acceleration Estimates.
## Code:
```python
import matplotlib.pyplot as plt  
  
flightData = []  
flightTimeStamps = []  
timeStampCol = 0  
stateMachineCol = 1  
barometer1Col = 22  
barometer2Col = 23  
barometerData = []  
times = []  
timesteps = []  
barometerSmoothData = []  
barometerVel = []  
barometerSmoothVel = []  
barometerAcc = []  
barometerSmoothAcc = []  
  
MA_WINDOWSIZE = 50  
  
with open("flightDataFile.txt", "r") as dataFile:  
    i = 0  
    for dataLine in dataFile.readlines():  
        if (dataLine.__contains__("HyDra")):  
            flightTimeStamps.append(i)  
            i+=1  
            continue  
        flightData.append(dataLine.split(","))  
        if (float(dataLine.split(",")[barometer1Col]) == 25778.78):  
            i+=1  
            continue  
        barometerData.append((float(dataLine.split(",")[barometer1Col]) + float(dataLine.split(",")[barometer2Col])) / 2.0)  
        times.append(float(dataLine.split(",")[0]))  
        i+=1  
    dataFile.close()  
  
barometerData = barometerData[317891 - 100:318662]  
times = times[317891 - 100:318662]  
  
#Barometer smoothing  
for i in range(0,len(barometerData)-MA_WINDOWSIZE):  
    sum  = 0.0  
    for d in range(MA_WINDOWSIZE):  
        sum += barometerData[i + d]  
    barometerSmoothData.append(sum / MA_WINDOWSIZE)  
  
for i in range(1,len(times)):  
    times[i] = (times[i] - times[0]) / 1000.0  
  
times[0] = 0  
  
for i in range(1,len(times)):  
    timesteps.append((times[i] - times[i-1]))  
  
for i in range(1,len(barometerSmoothData)):  
    barometerVel.append((barometerSmoothData[i] - barometerSmoothData[i - 1]) / timesteps[i])  
  
for i in range(1, len(barometerVel)):  
    barometerAcc.append((barometerVel[i] - barometerVel[i - 1]) / (timesteps[i] * 9.81))  
  
#Velocity Smoothing  
for i in range(0,len(barometerVel)-MA_WINDOWSIZE):  
    sum  = 0.0  
    for d in range(MA_WINDOWSIZE):  
        sum += barometerVel[i + d]  
    barometerSmoothVel.append(sum / MA_WINDOWSIZE)  
  
#Acceleration Smoothing  
for i in range(0,len(barometerAcc)-MA_WINDOWSIZE):  
    sum  = 0.0  
    for d in range(MA_WINDOWSIZE):  
        sum += barometerAcc[i + d]  
    barometerSmoothAcc.append(sum / MA_WINDOWSIZE)  
  
  
plt.subplot(3,1,1)  
plt.plot(times[:len(barometerSmoothData)], barometerSmoothData)  
#plt.plot(times[:len(barometerData)], barometerData)  
plt.ylabel("altitude [m]")  
plt.xlabel("time")  
plt.subplot(3,1,2)  
plt.plot(times[:len(barometerSmoothVel)], barometerSmoothVel)  
plt.ylabel("velocity [m / s]")  
plt.xlabel("timestamp")  
plt.subplot(3,1,3)  
plt.plot(times[:len(barometerSmoothAcc)], barometerSmoothAcc)  
plt.ylabel("acceleration [g]")  
plt.xlabel("timestamp")  
plt.show()  
  
#print(barometerData)
```
## Problems:
- The Moving Average Filter was implemeted on a sample based window, when it should have been implemented on a time based window. 
- The Moving Average Filter reduces duration of observation. To Fix this we should implement another Interpolator, like a LERP between distinct values for the values in between
### Structure of Solution:
First a high sampling frequency $f$ is chosen. Then, the Raw Barometer Output is sampled at $n/f$. As the Output has been discretized, we will have to LERP bewteen the last and the next Sample. This will yield a smoother curve, that is spaced correctly


