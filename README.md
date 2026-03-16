# Fitting Poisson  distribution
# Aim : 

To fit poisson distribution for the arrival of objects per minute from the feeder

# Software required :  

Python and Visual component tool

# Theory:

The Poisson distribution is the discrete probability distribution of the number of events occurring in a given time period, given the average number of times the event occurs over that time period.

![image](https://user-images.githubusercontent.com/104613195/166248326-fd042076-8b0b-40c4-8b11-1d8e8fcb74db.png)

 Conditions for Poisson Distribution:

1. An event can occur any number of times during a time period.
2. Events occur independently. I
3. The rate of occurrence is constant.
4. The probability of an event occurring is proportional to the length of the time period. 
 
# Procedure :

![image](https://user-images.githubusercontent.com/104613195/166251988-d0c53205-6080-4f7b-ae4c-398178586637.png)

# Experiment :

![image](https://user-images.githubusercontent.com/103921593/230282876-f4a5afbf-cac1-4648-a1b0-c78840638a8e.png)

# Program :
```
Exp 2:

import numpy as np
import math
import scipy.stats
L=[int(i) for i in input().split()]
N=len(L)
M=max(L) 
X=[]
f=[]
for i in range (M+1):
    c = 0
    for j in range(N):
        if L[j]==i:
            c=c+1
    f.append(c)
    X.append(i)
Sff=np.sum(f)
p=[]
for i in range(M+1):
    p.append(f[i]/Sff) 
mean=np.inner(X,p)
p=[]
E=[]
xi=[]
print("X P(X=x) Obs.Fr Exp.Fr xi")
print("--------------------------")
for x in range(M+1):
    p.append(math.exp(-mean)*mean**x/math.factorial(x))
    E.append(p[x]*Sff)
    xi.append((f[x]-E[x])**2/E[x])
    print("%2.2f %2.3f %4.2f %3.2f %3.2f"%(x,p[x],f[x],E[x],xi[x]))
print("--------------------------")
cal_chi2_sq=np.sum(xi)
print(f"Calculated value of Chi square is {cal_chi2_sq:.2f}")
table_chi2=scipy.stats.chi2.ppf(1-.01,df=M)
print(f"Table value of chi square at 1 level is {table_chi2:.2f}")
if cal_chi2_sq<table_chi2:
    print("The given data can be fitted in poisson Distribution at 1% LOS")
else:
    print("The given data cannot be fitted in Poisson Distribution at 1% LOS")
```

 

# Output : 
```
X P(X=x) Obs.Fr Exp.Fr xi
--------------------------
0.00 0.010 0.00 0.10 0.10
1.00 0.046 2.00 0.46 5.11
2.00 0.106 1.00 1.06 0.00
3.00 0.163 1.00 1.63 0.24
4.00 0.188 1.00 1.88 0.41
5.00 0.173 1.00 1.73 0.30
6.00 0.132 1.00 1.32 0.08
7.00 0.087 1.00 0.87 0.02
8.00 0.050 1.00 0.50 0.50
9.00 0.026 1.00 0.26 2.17
--------------------------
Calculated value of Chi square is 8.94
Table value of chi square at 1 level is 21.67
The given data can be fitted in poisson Distribution at 1% LOS
```

# Results

The Poisson distribution is fitted for the objects arrived from feeder per minute and the data is tested using Chi-square test. 
 
