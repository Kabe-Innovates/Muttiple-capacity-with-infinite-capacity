# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival  of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.

## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.

![image](https://user-images.githubusercontent.com/103921593/203238035-1c8109bc-cbf2-4c77-baea-c5b682a752ef.png)

## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)




## Experiment:
![image](https://github.com/user-attachments/assets/8224fba8-d758-4665-a06e-bc4cba2116aa)
![image](https://github.com/user-attachments/assets/153d7d96-e10d-4440-955a-ebfe156f4d3e)


## Program :
```python
# Getting Inputs
ArrivalTime = float(input("Enter the mean inter arrival time of objects from Feeder (in secs): "))
ServiceTime = float(input("Enter the mean inter service time of Lathe Machine (in secs): "))
RobotTime = float(input("Enter the Additional time taken for the Robot (in secs): "))
NumberOfServers = int(input("Number of service centre : "))

# Calculating Lambda and Mu
Lambda = 1 / ArrivalTime
Mu = 1 / (ServiceTime + RobotTime)

print("Multiple Server with Infinite Capacity - (M/M/c):(∞/FIFO)")
print("The mean arrival rate per second : %0.2f" % Lambda)
print("The mean service rate per second : %0.2f" % Mu)

# Utilization factor
Rho = Lambda / (NumberOfServers * Mu)

# Calculating P0 (Probability system is empty)
sum_terms = 0
for i in range(NumberOfServers):
    sum_terms += (Lambda / Mu) ** i / math.factorial(i)

last_term = ((Lambda / Mu) ** NumberOfServers) / (math.factorial(NumberOfServers) * (1 - Rho))
TotalSum = sum_terms + last_term
P0 = 1 / TotalSum

# System performance measures (M/M/c)
if Rho < 1:
    Lq = ((P0 * ((Lambda / Mu) ** NumberOfServers) * Rho) /
          (math.factorial(NumberOfServers) * ((1 - Rho) ** 2)))
    Ls = Lq + (Lambda / Mu)
    Ws = Ls / Lambda
    Wq = Lq / Lambda

    print("Average number of objects in the system : %0.2f" % Ls)
    print("Average number of objects in the conveyor :  %0.2f" % Lq)
    print("Average waiting time of an object in the system : %0.2f secs" % Ws)
    print("Average waiting time of an object in the conveyor : %0.2f secs" % Wq)
    print("Probability that the system is busy : %0.2f" % Rho)
    print("Probability that the system is empty : %0.2f" % (1 - Rho))
else:
    print("Warning! Objects Over flow will happen in the conveyor")

```
## Output :
```
--------------------------------------------------------------
Multiple Server with Infinite Capacity - (M/M/c):(∞/FIFO)
--------------------------------------------------------------
The mean arrival rate per second : 0.10
The mean service rate per second : 0.12
Average number of objects in the system : 0.95
Average number of objects in the conveyor :  0.15
Average waiting time of an object in the system : 9.53 secs
Average waiting time of an object in the conveyor : 1.52 secs
Probability that the system is busy : 0.40
Probability that the system is empty : 0.60
--------------------------------------------------------------
```

## Result : 
Thus the program is implemented and executed successfully.

