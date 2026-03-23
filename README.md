# Algorithm for QR Decomposition
## Aim:
To implement QR decomposition algorithm using the Gram-Schmidt method.
## Equipment’s required:
1.	Hardware – PCs
2.	Anaconda – Python 3.7 Installation / Moodle-Code Runner
## Algorithm:
1.	Intialize the matrix Q and u
2.	The vector u and e is given by

    ![eqn1](./ex4.jpg)

    ![eqn2](./ex6.jpg)

    ![eqn3](./ex3.jpg)

3.	Obtain the Q matrix   
    ![eqn4](./ex1.jpg)
4.	Construct the upper triangular matrix R
    ![eqn5](./ex2.jpg)



## Program:
### Gram-Schmidt Method
```
import os
os.environ["OPENBLAS_NUM_THREADS"]="1"
import numpy as np

def QR_Decomposition(A):
    n, m = A.shape
    
    Q = np.zeros((n, m))
    R = np.zeros((m, m))
    
    for i in range(m):
        u = A[:, i]
        
        for j in range(i):
            R[j, i] = np.dot(Q[:, j], A[:, i])
            u = u - R[j, i] * Q[:, j]
        
        R[i, i] = np.linalg.norm(u)
        Q[:, i] = u / R[i, i]
    
    print("The Q Matrix is\n", Q)
    print("The R Matrix is\n", R)


a = np.array(eval(input()))
QR_Decomposition(a)


```

## Output

<img width="1920" height="1080" alt="Screenshot 2026-03-23 230827" src="https://github.com/user-attachments/assets/03a0ec14-178d-49d3-b2b6-5817054c6b05" />



## Result
Thus the QR decomposition algorithm using the Gram-Schmidt process is written and verified the result.
