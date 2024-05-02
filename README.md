# Ex.No: 02 LINEAR AND POLYNOMIAL TREND ESTIMATION
### Date: 24/02/24
### AIM:
To Implement Linear and Polynomial Trend Estiamtion Using Python.

### ALGORITHM:
1. Import necessary libraries (NumPy, Matplotlib)

2. Load the dataset

3. Calculate the linear trend values using least square method

4. Calculate the polynomial trend values using least square method

4. End the program
### PROGRAM:
#### A - LINEAR TREND ESTIMATION
~~~
## Trend equation using Linear Equation

import numpy as np
from tabulate import tabulate
x = [2010, 2012, 2014, 2016, 2018]
y = [18, 21, 23,27,16]
X = [i - x[len(x)//2] for i in x] 
x2 = [i ** 2 for i in X]
xy = [i * j for i, j in zip(X, y)]

table = [[i, j, k, l, m] for i, j, k, l, m in zip(x, y, X, x2, xy)]

print(tabulate(table, headers=["Year", "Prod", "X=x-2014", "X^2", "xy"], tablefmt="grid"))

n=len(x)
b=(n*sum(xy)-sum(y)*sum(X))/(n*sum(x2)-(sum(X)**2))
a=(sum(y)-b*sum(X))/n
print("a=%.1f,b=%.1f"%(a,b))
l=[]
for i in range(n):
  l.append(a+b*X[i])
print(l)
print("Trend Equation : y=%d+%.2fx"%(a,b))
import matplotlib.pyplot as plt
plt.title("Linear Trend Graph")
plt.xlabel("Year")
plt.ylabel("Production")
plt.plot(x,l)
~~~
#### B- POLYNOMIAL TREND ESTIMATION
~~~
## Polynomial TRend EStimation 4th degree

import numpy as np
from tabulate import tabulate
x = [2011,2012,2013,2014,2015,2016]
y = [100,107,128,140,181,192]
X = [2*(i-(sum(x)/len(x))) for i in x]
x2 = [i ** 2 for i in X]
xy = [i * j for i, j in zip(X, y)]
x3 = [i ** 3 for i in X]
x4 = [i ** 4 for i in X]
x2y=[i*j for i,j in zip(x2,y)]

table = [[i, j, k, l, m,n,o,p] for i, j, k, l, m,n,o,p in zip(x, y, X, x2, x3,x4,xy,x2y)]

print(tabulate(table, headers=["Year", "Prod", "X=x-2013", "X^2", "X^3","X^4","xy","x2y"], tablefmt="grid"))
coeff=[[len(X),sum(X)],[sum(X),sum(x2)]]

coeff=[[len(x),sum(X),sum(x2)],[sum(X),sum(x2),sum(x3)],[sum(x2),sum(x3),sum(x4)]]
Y=[sum(y),sum(xy),sum(x2y)]
A=np.array(coeff)
B=np.array(Y)
try:
  solution=np.linalg.solve(A,B)
except:
  print("error")
a,b,c=solution
print("a=%.2f, b=%.2f, c=%.2f"%(a,b,c))
print("Polynomial trend equation y=%.2f+%0.2fx+%.2fx^2"%(a,b,c))
l=[]
for i in range(len(X)):
  l.append(a+b*X[i]+c*x2[i])
import matplotlib.pyplot as plt
plt.plot(x,l)
~~~
### OUTPUT
#### A - LINEAR TREND ESTIMATION
![](https://github.com/RanjithD18/TSA_EXP2/blob/main/1.png)
![](https://github.com/RanjithD18/TSA_EXP2/blob/main/2.png)
#### B- POLYNOMIAL TREND ESTIMATION
![](https://github.com/RanjithD18/TSA_EXP2/blob/main/3.png)
![](https://github.com/RanjithD18/TSA_EXP2/blob/main/4.png)

### RESULT:
Thus the python program for linear and Polynomial Trend Estiamtion has been executed successfully.
