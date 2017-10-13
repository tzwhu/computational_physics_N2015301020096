>*  由于一直未能成功安装pygame
![image](https://user-images.githubusercontent.com/31878522/31556645-6a1a7990-b078-11e7-84e5-c082721dadfd.png)，<br>
拟写了：“以45度出射，初速度300m/s，重力加速度取为10m/s^2”的轨迹程序。<br>
在这个程序中，背景为一拟'sky'的图片；<br>
炮弹的图案为一拟'cannon'的图片。<br>
> * **代码部分:**


> 调用模块，设置画面：

     import pygame 
     import math
     from sys import exit  
     pygame.init()
     screen = pygame.display.set_mode((800, 800), 0, 32)
     pygame.display.set_caption("cannon")
     pygame.mouse.set_visible(False)
 > 调用图片：
 
     background = pygame.image.load(background_image_filename).convert()
     cannon = pygame.image.load(cannon_image_filename).convert_alpha()
> 设置初始坐标：

     cannon_x, cannon_y = 0, 0
     clock = pygame.time.Clock()
     while True:
         for event in pygame.event.get():
             if event.type == pygame.QUIT:
             pygame.quit()
             exit()
   
    screen.blit(background, (0,0))
>    在画布范围内，计算抛物线轨迹：

    if cannon_y < 799 :
    degree=45
    V=300
    g=10
    a=math.radians(degree)
    COS=math.cos(a)
    SIN=math.sin(a)
    VXI=V*COS
    VYI=V*SIN
    VX=VXI
    VY=VYI
    TIME=0
    deta=0.01
    X=0
    Y=0
    x=[0]
    y=[0] 
    time=[0]
    vx=[VXI]
    vy=[VYI]
> 计算当前时间的坐标：

    while TIME<clock:
    TIME=TIME+deta
    VX=VX
    Y=Y+VY*deta
    VY=VY-g*deta
    X=X+VX*deta
    time.append(TIME)
    vx.append(VX)
    vy.append(VY)
    x.append(X)
    y.append(Y) #
> 将坐标赋给炮弹的图片

        cannon_x, cannon_y = x[-1], y[-1]
    else:
>    刷新画面：

       pygame.display.update()


