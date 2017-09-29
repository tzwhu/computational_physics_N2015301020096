import pylab as pl <br>
NA=100<br>
NB=0<br>
TIME=0<br>
deta=0.01<br>
time=[0]<br>
ya=[100]<br>
yb=[0]<br>
while TIME<=50:<br>
    TIME=TIME+deta<br>
    NA=NA+(NB-NA)*deta<br>
    NB=NB+(NA-NB)*deta<br>
    time.append(TIME)<br>
    ya.append(NA)<br>
    yb.append(NB)<br>
else:<br>
    print ("deta=",deta,"s")<br>
    plot1=pl.plot(time,ya,label='NA')<br>
    plot2=pl.plot(time,yb,label='NB')<br>
    pl.title('Question *1.5 ')<br>
    pl.xlabel('time/s')
    pl.ylabel('N')
    pl.xlim(0, 52)
    pl.ylim(0, 110)
    pl.legend(loc = 'best')
pl.show()
