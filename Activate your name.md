# 使你的名字在屏幕上移动起来
##  使用Python中的Tkinter模块
> * 让字母以二次曲线y=x^2移动到(20,400)坐标，然后以直线返回原点。<br>
> * 设置字母的字体为20的Times字体。<br>
> * 结束后输出“”end“”<br>
### 实现流程

```flow
st=>start: 调用Tkinter和 time 模块，布置画布
op=>operation: 用font设置字体
a=>operation: 计数参量i=1
b=>operation: 移动坐标实现二次曲线
d=>operation: 刷新和延时，i=i+1
cond=>condition: 判定i<=20
f=>operation: 遍历重复，向原点移动小段
g=>operation: 刷新和延时，多次后返回，输出“end”
e=>end


st->op->a->b->d->cond
cond(yes)->f->g->e
cond(no)->a
```
