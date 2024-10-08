# Assignment-2
# Calculation of total Infiltration by Horton's Equation
fo=float(input("Enter the value of initial Infiltration Rate:"))
fc=float(input("Enter the value of Final infiltration Rate:"))
t=int(input("Enter the value of Time:"))
kh=float(input("Enter the value of Decay Coefficient:"))
# The total Infiltration is given by:
Fp=fc*t+(fo-fc)/kh
print("The value of Total Infiltration is:",Fp)
#Q-2
#Calculation of Mean precipitation by Theissen's Polygon Method
#The value of precipitation at Each station is
p1=int(input("Enter the value of rainfall at Station 1:"))
p2=int(input("Enter the value of rainfall at Station 2:"))
p3=int(input("Enter the value of rainfall at Station 3:"))
p4=int(input("Enter the value of rainfall at Station 4:"))
p5=int(input("Enter the value of rainfall at Station 5:"))
#The total precipitation is
p=p1+p2+p3+p4+p5
print("The value of Total Precipitations is:",p)
#Area for each station
A1=int(input("Enter the value of Catchment Area for raingauge station 1:"))
A2=int(input("Enter the value of Catchment Area for raingauge station 2:"))
A3=int(input("Enter the value of Catchment Area for raingauge station 3:"))
A4=int(input("Enter the value of Catchment Area for raingauge station 4:"))
A5=int(input("Enter the value of Catchment Area for raingauge station 5:"))
#The total catchment area is
A=A1+A2+A3+A4+A5
print("The value of Total Catchment area is:",A)
# Runoff Volume
#The volume shall be multiplied by the coefficient 2500 to cater scale effects
#Runoff Volume
V=(p1*A1+p2*A2+p3*A3+p4*A4+p5*A5)*2500
print("The runoff volume from the given catchment is:",V)
# Mean Precipitation
p*(p1*A1+p2*A2*p3*A3+p4*A4+p5*A5)/A
print("The value of Mean Precipitalon is:",p)
#Q-3
#Calculation of Mean precipitation by Isohytel Method
#The value of precipitation at Each station i
p1=int(input("Enter the value of rainfall at Station 1:"))
p2=int(input("Enter the value of rainfall at Station 2:"))
p3=int(input("Enter the value of rainfall at Station 3:"))
p4=int(input("Enter the value of rainfall at Station 4:"))
p5=int(input("Enter the value of rainfall at Station 5:"))
p6=int(input("Enter the value of rainfall at Station 6:"))
p7=int(input("Enter the value of rainfall at Station 7:"))
p8=int(input("Enter the value of rainfall at Station 8:"))
# Area for each station
A1=int(input("Enter the value of Catchment Area for raingage station 1:"))
A2=int(input("Enter the value of Catchment Area for raingauge station 2:"))
A3=int(input("Enter the value of Catchment Area for raingauge station 3:"))
A4=int(input("Enter the value of Catchnent Area for reingauge station 4:"))
A5=int(input(" Enter the value of Catchment Ares for raingauge station 5:"))
A6=int(input("Enter the value of Catchment Area for raingeuge station 6:"))
A7=int(input("Enter the value of Catchment Area for reingauge station 7:"))
# The total catchment area is
A=A1+A2+A3+A4+A5+A6+A7
print("The value of Total Catchment area is:",A)
# The total precipitation is
p=p1+p2+p3+p4+p5+p6+p7+p8
# Mean Precipitation
p=((p1+p2)*A1/2+(p2+p3)*A2/2+(p3-p4)*A3/2+(p4+p5)* A4/2+(p5+p6)*A5/2+(p6+p7)*A6/2
+(p7+p8)*A7/2)/A
print("the value of Mean Precipitalon is:",p)
#Q-4
import numpy as geek
N=int(input("Number of data values of rainfall:"))
M=int(input("Number of data values of Area:"))
R=[]
A=[]
for i in range (1, N+1):
  print("Enter rainfall in cm:")
  Value_rainfall=float(input())
  R.append(Value_rainfall)
for j in range (1, M+1):
  print("Enter Catchment area:")
  Value_area=float(input())
  A.append(Value_area)
product=geek.dot(R,A)
# print("Dot Product:\n",product)
mean_precipitation=product/sum(A)
print("Mean Precipitation:",mean_precipitation,"cm")
#Q-5
import numpy as np
N=int(input("Number of pulses:"))
dt=float(input("Enter time interval of each pulse in hours :"))
Rd=float(input("Enter the value of runoff depth (Rd) in cm:"))
Ri=[]
#Rainfall Intensity
for i in range (1, N+1):
  print("Enter rainfall intensity in cm/hr for pulse:".format(i))
  Value=float(input())
  Ri.append(Value)
print("W-Index calculation")
Total_Rain=sum(Ri)*dt
print("Total depth of rainfall={}cm".format(Total_Rain) )
W_index=(Total_Rain-Rd)/(N*dt)
print("W-index=cm/hr".format(W_index))
print("Phì-Index Calculation")
def excess_rain (M,Ri,tr):
  print("Trail No:",tr)
  print("Assume that out of{}pulses, pulses have rainfall excess".format(N, M))
  te=dt*M
  print("Duration of excess rainfall={}hrs".format(te))
  R_depth=0
  for j in range (0, M):
    R_depth=sum(np.dot(Ri, dt))
    print("Total depth of excess rainfall for trial",tr,"=",R_depth,"cm")
    phi=(R_depth-Rd)/te
    print("Phi Index for trial",tr, "=",phi,"cm/hr")
    Ri.sort()
    print("Ri (sorted)=",Ri)
    return phi
M=N
tr=0
 #trail no
while(0<M<=N):
  tr+=1
  phi=excess_rain (M,Ri,tr) #driver function
  print("While loop Ri =",Ri)
  print("While loop Phi-",phi)
  M-=1
if (Ri[0]>phi):
  print("\nFinal value of Phi-index={}cm/hr".format(phi))
else:
  print("As rainfall intensity {} cm/hr<O,so no contributiontowards runoff".format(Ri[0],phi)) # Changed Ø to 0
  del Ri[0] # Changed Ø to 0
  print("Assumption of {}pulses have rainfal1 excess fails, soremove least rainfall intensity <()". format (M, phi))
  print("Excess rainfall intensities (sorted):",Ri)
  print("In next trial ass ume no. of pulses that have rainfallexcess:",len(Ri))0
