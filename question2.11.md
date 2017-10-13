# 2.11 微小变化对抛物线的影响

标签： P31

---
## 结果展示：
>* 速度出现微增时（1%），射程差随角度的变化

**10m/s-960m/s    detaV=50m/s**

![image](https://user-images.githubusercontent.com/31878522/31550415-d7283118-b063-11e7-9536-07b8390640b6.png) ![image](https://user-images.githubusercontent.com/31878522/31546442-e92f4832-b055-11e7-98d1-ec89fc22f501.png)<br>
**0.1m/s-10m/s   detaV=0.5m/s**

![image](https://user-images.githubusercontent.com/31878522/31549085-a2b461ee-b05f-11e7-85a1-592c94a68643.png)![image](https://user-images.githubusercontent.com/31878522/31550754-f577650c-b064-11e7-9c2a-2e1c12f489fd.png)

>* 出现+10km/h的风力作用时，射程差随角度的变化

**10m/s-960m/s    detaV=50m/s**

![image](https://user-images.githubusercontent.com/31878522/31550499-1f3a8622-b064-11e7-9d86-80078d938516.png) ![image](https://user-images.githubusercontent.com/31878522/31546442-e92f4832-b055-11e7-98d1-ec89fc22f501.png)<br>
**0.1m/s-10m/s   detaV=0.5m/s**

![image](https://user-images.githubusercontent.com/31878522/31551742-115c1148-b068-11e7-9be6-e1fe148ad96b.png)![image](https://user-images.githubusercontent.com/31878522/31550754-f577650c-b064-11e7-9c2a-2e1c12f489fd.png)

> * 出现-10km/h的风力作用时，射程随角度的变化

**10m/s-960m/s    detaV=50m/s**

![image](https://user-images.githubusercontent.com/31878522/31550499-1f3a8622-b064-11e7-9d86-80078d938516.png) ![image](https://user-images.githubusercontent.com/31878522/31546442-e92f4832-b055-11e7-98d1-ec89fc22f501.png)<br>
**0.1m/s-10m/s   detaV=0.5m/s**

![image](https://user-images.githubusercontent.com/31878522/31550980-b6f27e24-b065-11e7-8812-986976be6ff3.png)![image](https://user-images.githubusercontent.com/31878522/31550754-f577650c-b064-11e7-9c2a-2e1c12f489fd.png)

>* 有正向风来的变动率曲线（change rate-degree）:
**0.5m/s-10m/s**
![image](https://user-images.githubusercontent.com/31878522/31554321-c84c9682-b06f-11e7-81d6-7cd6e72e650d.png)
>* 有反向风来的变动率曲线（change rate-degree）:
**0.5m/s-10m/s**
![image](https://user-images.githubusercontent.com/31878522/31553819-411a1910-b06e-11e7-91c2-168d7cfe523b.png)
> * 速度微增的变动率曲线（change rate-degree）:
![image](https://user-images.githubusercontent.com/31878522/31554674-e22bb1d6-b070-11e7-876f-9b5120f9a872.png)

## 实现思路：
>*	设计循环，以欧拉法计算一固定出射角度，出射速度，重力加速度的抛物线轨道，并计算落点；
>*	将循环改写为函数   f1(a,b,c)，
含有自变量为(degree, V, g),它给出的是只有重力作用的射程；
>*	引入风阻，利用教材提供的公式，
得到函数 f2(a,b,c), 它给出的考虑风阻的射程；
>*	定义函数m和函数n：
m用来计算出射速度提高1%的射程差；
n用来计算考虑风阻作用时的射程差;
>* m(a,b,c) = f1(a,b*1.01,c)-f1(a,b,c)
   n(a,b,c) = f2(a,b,c)-f1(a,b,c)
>* 以角度为自变量，对一固定出射速度，作图(deta S-degree);



## 实现程序：
**Ⅰ.仅重力作用：[源代码](https://github.com/tzwhu/computational_physics_N2015301020096/blob/master/cannon%20code1.txt)**
> 调用模块：

     import pylab as pl  
     import math
> 定义函数：

    def f1(a,b,c):
          degree=a
          V=b
          g=c
> 角度弧度转换：

    a=math.radians(degree)
    COS=math.cos(a)
    SIN=math.sin(a)
    ...
> 计算部分：

         VX=VX
         Y=Y+VY*deta
         VY=VY-g*deta
         X=X+VX*deta
         ...
> 计算落点：

        xlast=x[-1]
        xlast2=x[-2]
        ylast=y[-1]
        ylast2=y[-2]
        r=-(ylast/ylast2)
        xl=(xlast+r*xlast2)/(r+1)
        ...

> 对所有计算结果统一取三位有效数字：

        S=round(xl,3)
        return S


**Ⅱ考虑风阻：[源代码](https://github.com/tzwhu/computational_physics_N2015301020096/blob/master/cannon%20code2.txt)**
> 调用各模块;


> 定义函数和风速（正风速自左向右）：

    def f2(a,b,c):
       degree=a
       V0=b
       VW=25/9
       …
> 角度弧度转换;
    
> 计算部分：

        V=math.sqrt(VX**2+VY**2)
        a=(V-35)/5
        E=1+math.exp(a)
        MDV=math.sqrt((VX-VW)**2+VY**2)
        b=0.0039+0.0058/E
        X=X+VX*deta
        Y=Y+VY*deta
        VX=VX-b*MDV*(VX-VW)*deta
        VY=VY-b*MDV*VY*deta-g*deta
        …
> 计算落点;

        
    
**Ⅲ.作图程序（双循环）[源代码](https://github.com/tzwhu/computational_physics_N2015301020096/blob/master/cannon%20%20code3.txt)**
> 创造网格背景：

     pl.figure(1)
     pl.style.use('bmh')
    ...
> 设置坐标范围，标题等参数；
> 外循环变量：初速

    vtest=700
    VTEST=[]
    while vtest<=1000:
> 内循环变量：出射角度

    degreeTEST=1
    DEGREETEST=[degreeTEST]
    detas=n(degreeTEST,vtest,10)
    DETAS=[detas]
    while degreeTEST<=89:
    ...
> 内循环结束
         
    else:
         r=vtest
         pl.plot(DEGREETEST,DETAS,label=r)
         vtest=vtest+50
> 外循环结束：

     else:
        pl.legend(loc = 'best')
        pl.show() 
        print("over")
        
## 程序分析：
> * 在实现编程中发现，python对空格的使用有较为严格的要求；
在使用的二重循环中，while和else语句的位置容易造成报错。
> * 由题意可知，在风向为反向时，即使出射角为90度，仍然会有一正的射程差；在曲线的最右端因此产生“断崖”状的图像
![image](https://user-images.githubusercontent.com/31878522/31550980-b6f27e24-b065-11e7-8812-986976be6ff3.png)
> * 在在风向为正向时，当出射角为90度，会有一负的射程差；在曲线的最右端因此在90度之前交于x轴，并进入Y<0的区域。
![image](https://user-images.githubusercontent.com/31878522/31551742-115c1148-b068-11e7-9be6-e1fe148ad96b.png)

## 结论：
> * 两种微小变化情景对炮弹射程均有影响
> * 两种情景在出射速度较高时造成的差异巨大；风正向吹来时，射程变化更加显著。
> * 增加风力作用时，变动率随着速度发生变化
> * 速度微增时，变动率几乎不发生变化




