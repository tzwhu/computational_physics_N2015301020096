# Question *1.5
标签： P16-P17 

---
## 以欧拉法解决两种粒子的数量变化问题（NA/NB）
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
### 计算过程：
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




