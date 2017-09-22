import time
 from tkinter import*
    tk = Tk()
    canvas = Canvas(tk,width=25,height=405)
    canvas.pack()
    canvas.create_text(0,0,text='tangzhe',font=('Times',20))
	
	i=1
while i<=20:
    canvas.move(1,1,i*2-1)  
    tk.update()              
    time.sleep(0.05) 
    i=i+1
else:
	for a in range(0,20)	
    canvas.move(1,-1,-20) 
    tk.update()             
    time.sleep(0.05)
    print("end")
