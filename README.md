# 基于PythonTkinter 实现选择是否播放
### 可配合任务计划程序实现定时播放
自己做的一个简单程序，可能有用
### 预览
[![效果展示.jpg](https://s1.ax1x.com/2023/02/03/pSscO1J.jpg)](https://imgse.com/i/pSscO1J)

```python
import os
import time
from tkinter import *
import sys
import tkinter
import threading

def open():
    os.startfile(r'C:\xx.mp4')  #设置文件路径
    sys.exit()

def off():
    sys.exit()

window = Tk()
window.protocol('WM_DELETE_WINDOW',off) 
window.title("提醒")
window.geometry("600x200+400+200")
lbl = Label(window, text="即将播放", font=("微软雅黑", 36))
lbl.place(x=150, y=0)
btn = Button(window, text="确定", command=open)
btn.place(x=100, y=100)
bt = Button(window, text="取消", command=off)
bt.place(x=500, y=100)

lbTime=tkinter.Label(window,fg='red',anchor='w',font=("微软雅黑", 18))
lbTime.place(x=200,y=80,width=190)

def autoClose():
    for i in range(5):
        lbTime['text']='距离播放还有{}秒'.format(5-i)
        time.sleep(1)
    window.destroy()
#默认5s，可自行修改
t=threading.Thread(target=autoClose)
t.start()

window.mainloop()
open()

```

