# 2.21 弧线球的轨迹问题

标签（空格分隔）： 未分类

---

## 结果展示： Z-X平面内的轨迹
>* 此次问题要求研究的是在**一定恒自转速度**的作用下，研究旋转对其轨迹的影响：
>* 在之后的讨论中将原点取在出射点，故不再考虑出射高度的影响
>* 影响该轨迹的因素有  **出射角度(degree)** 和  **出射速度（V）** <br>


( 作出球飞行轨迹的**俯视图**研究 )
![image](https://user-images.githubusercontent.com/31878522/31812756-a2ba5f7a-b5b6-11e7-9659-c3acefaff155.PNG)



**说明：我们将在下面的图示中，将其他因素作为自变量，画出z-x平面内的不同轨迹**
>* **每一张子图中所有轨迹初速相同；以不同颜色的线，代表不同的出射角度比较，单位是°**
>* **每一张子图中左方的注释，代表的是该图中（多条线）的共同初速度，单位是m/s**

![image](https://user-images.githubusercontent.com/31878522/31821432-ad95d69c-b5d7-11e7-98fc-8f0770324448.png) 

>* **每一张子图中所有轨迹出射角速度相同；以不同颜色的线，代表不同的初速度比较，单位是m/s**
>* **每一张子图中左方的注释，代表的是该图中（多条线）的共同出射角度，单位是°**

![image](https://user-images.githubusercontent.com/31878522/31821119-95fca020-b5d6-11e7-9476-b8d8e15b2aeb.png) 


> * **在高的出射速度下(1000m/s)**
 
![image](https://user-images.githubusercontent.com/31878522/31810243-95b7fc78-b5ad-11e7-9cbd-a93f0520aa78.PNG)


## 实现程序：
**Ⅰ.[源代码](https://github.com/tzwhu/computational_physics_N2015301020096/blob/master/2.21%20.txt)**
**Ⅱ.计算部分**
>* 计算(X,Y,Z)和(VX,VY,VZ)：
        
        ...
        X=X+VX*deta                     
        Y=Y+VY*deta
        Z=Z+VZ*deta
        
        VX=VX-b*V*VX*deta
        VY=VY-10*deta
        VZ=VZ-10*u*VX*w*deta
        ...
        
## 结论：
> * 球的旋转（问题中自转方向）会给球的轨迹带来侧向的位移
> * 其他条件相同，出射速度不同时，轨迹有差异；速度更高时，球轨迹的弯曲程度更小。
> * 其他条件相同，出射角度不同时，轨迹有差异；出射角度更小时，球轨迹的弯曲程度更小。




