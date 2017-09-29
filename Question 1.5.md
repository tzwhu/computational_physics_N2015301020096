# Question 1.5:以欧拉法解决两种粒子的数量变化问题（NA/NB）
标签： P16-P17 

---

### 实现流程
> * 设置变量 NA,NB，时间TIME,时间间隔deta
> * 设置数组 x,ya,yb 分别记录多次循环中的时间,两种粒子的粒子数
> * 赋值两种粒子的初始值 NA=100，NB=0 
> * 对粒子数量变化的公式以欧拉法改写
> * 循环计算deta ,2deta...各时刻的粒子数
> * 用 append() 语句将结果赋予数组 x,yza,yb
> * 调用plot语句作图，完善说明

### 计算结果示例( deta=0.01s )
![image](https://user-images.githubusercontent.com/31878522/31002566-0f9cf3c2-a51e-11e7-8a2f-066246d829e4.PNG)
### 计算过程： [源代码](https://github.com/tzwhu/computational_physics_N2015301020096/blob/master/02%20code)
> * 欧拉法计算

    NA=NA+(NB-NA)*deta 
    NB=NB+(NA-NB)*deta
> * 循环赋予数组过程    

    time=[0]
    ya=[100]
    yb=[0]                #记录初状态
    ...
    time.append(TIME)     #记录时间
    ya.append(NA)         #记录NA
    yb.append(NB)         #记录NB
    ...
> * 完善图示

    plot1=pl.plot(time,ya,label='NA')     #设置曲线名称
    plot2=pl.plot(time,yb,label='NB')     
    pl.title('Question *1.5 ')            #设置图示标题
    pl.xlabel('time/s')                   #设置x轴名称
    pl.ylabel('N')
    pl.xlim(0, 52)                        #设置图示区域大小
    pl.ylim(0, 110)
    pl.legend(loc = 'best')               #设置标签
    pl.show()
## 结果分析
1.误差分析：
当deta接近题中所述的时间常数1s时，结果将无法连续变化产生较大误差。<br>
如取1s，此时计算结果将退化为（t，NA,NB）=(1，0，0)<br>
之后粒子数皆不变，NA,NB始终为0<br>
但事实上将题中两微分式相加，d（NA+NB）/dt=0,即两粒子之和不随时间变化，在任意时刻都为100。<br>
结果显然不对。
>误差来自于：
> * 当由第一个算式计算完NA，实际上此时已是1*deta时的NA（而非初值）代入下一式计算NB。
> * 若deta选取过大，如1s时，计算后NA直接为0，与初值相差甚远。
> * 图像将退化为

![image.1](https://user-images.githubusercontent.com/31878522/31004854-c613879c-a528-11e7-8af9-c42d9a31ecf5.PNG)

> * 减小误差的方法：选择更小的deta，以获得更精确的结果。
> * 不同deta时的图像对比：( deta从大到小)

![image.2](https://user-images.githubusercontent.com/31878522/31002878-930c47ac-a51f-11e7-9a55-bda188ac4d5c.PNG)
![immage.3](https://user-images.githubusercontent.com/31878522/31002713-d30b2d2e-a51e-11e7-9647-95a039892fb2.PNG)
![image.4](https://user-images.githubusercontent.com/31878522/31002693-b40c748c-a51e-11e7-82a7-405ce2ee312a.PNG)
![image.5](https://user-images.githubusercontent.com/31878522/31002609-4dbbac16-a51e-11e7-9e7a-62caf9737326.PNG)
![image.6](https://user-images.githubusercontent.com/31878522/31002537-e188883e-a51d-11e7-81c3-46390dfe24b3.PNG)
![image.7](https://user-images.githubusercontent.com/31878522/31002566-0f9cf3c2-a51e-11e7-8a2f-066246d829e4.PNG)

2.结果的检验
> * 两粒子数在任意时间之和应为100不变
> * 在足够长的时间后，NA=NB，粒子数应都趋向于50<br>
当deta足够小（=0.01s时），符合以上检验要求
> * 与精确解的图像对比
该方程的解析解为<br>
NA=50+50e^(-2t)<br>
NB=50-50e^(-2t)<br>














