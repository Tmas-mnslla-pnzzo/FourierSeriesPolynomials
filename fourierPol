import numpy as np
import matplotlib.pyplot as plt
import math

pi=np.pi

def fact(n):
    f=math.factorial(n)
    return f

def a_k(k,m):
    if m%2==0:
        if k!=0:
            i=int(m/2)
            u=0
            s=0
            for item in range(i):
                s=s+(((-1)**(i+k+u-1))*(fact(2*i))*(pi**(2*u)))/((k**(2*(i-u)))*(fact(2*u+1)))
                u=u+1
            a=2*s
        else:
            a=(2*(pi**(m)))/(m+1)
    else:
        a=0
    return a

def b_k(k,n):
    if n%2!=0:
        if k!=0:
            i=int((n+1)/2)
            u=0
            s=0
            for item in range(i):
                s=s+(((-1)**(i+k+u))*(fact(2*i-1))*(pi**(2*u)))/((k**(2*(i-u)-1))*(fact(2*u+1)))
                u=u+1
            b=2*s
        else:
            b=0
    else:
        b=0
    return b

def fourier(x,g,ter):
    s=a_k(0,g)/2
    for k in range(1,ter):
        s=s+a_k(k,g)*np.cos(k*x)+b_k(k,g)*np.sin(k*x)
    return s

def fourierPOL(x,g,v,ter):
    f=v[0]
    for a in range(g):
        f=f+v[a+1]*fourier(x,a+1,ter)
    return f

def labelP(coef,g):
    if coef[0]!=0:
        strr=f'{coef[0]}'
    else:
        strr=''
    for h in range(g):
        if coef[h+1]!=0:
            if coef[h+1]<0 or strr=='':
                e=''
            elif coef[h+1]>0:
                e='+'
            if (h+1)!=1:
                strr=strr + e +f'{coef[h+1]}x^{h+1}'
            else:
                strr=strr + e +f'{coef[h+1]}x'
        else:
            strr=strr+''
    return strr

def pol(v,m,x):
    p=0
    for z in range(0,m+1):
        p=p+(x**z)*v[z]
    return p

def iniciar():
    g=int(input("Ingrese el grado: "))
    coef=[]
    for c in range(g+1):
        coef.append(int(input(f"ingrese el coeficiente {c}: ")))
    ter=int(input("Ingrese la cantidad de terminos para la aproximación: "))
    return g,coef,ter

def graficar(vari):
    g=vari[0]
    coef=vari[1]
    ter=vari[2]
    X=[]
    Y1=[]
    Y2=[]
    for x in range(-360,360):
        X.append(x/100)
    for s in X:
        Y1.append(pol(coef,g,s))
        Y2.append(fourierPOL(s,g,coef,ter))
    plt.plot(X,Y2)
    plt.plot(X,Y1)
    plt.legend([f'Serie de Fourier de p(x) con {ter} terminos.', f'p(x)=${labelP(coef,g)}$']) 
    plt.show()

graficar(iniciar())

