# Tkinter GUI MD5 sha1计算程序

  
## 程序运行效果
![image]( http://s5.51cto.com/wyfs02/M01/77/55/wKiom1ZmqOmBCXljAAAqtB0EMRg993.png)

## python 代码
```
#coding: UTF-8
#图形化 字符串MD5 Sha1加密
import Tkinter as tk
import hashlib
def F_md5(str_mh): #md5 sha1计算方法
    str_mh=str_mh.encode("UTF-8") #将获得的值转换为UTF-8编码
    
    #md5校验值计算
    md5=hashlib.md5()
    md5.update(str_mh)
    
    #SHA1校验值计算
    sha1=hashlib.sha1()
    sha1.update(str_mh)
        
    fmd5=md5.hexdigest()  #生成字符串 MD532校验值
    fmd516=fmd5[8:24]     #生成字符串 MD516校验值
    fsha1=sha1.hexdigest()#生成字符串 SHA1校验值

    mh=[fmd516,fmd5,fsha1] #将生成的 md516、md532、sha1存入数组
    return mh
    
def view_md5():  #计算结果显示方法
        
    md5=e1.get() #获取entry组件内的内容，也就是获取输入值
    mh=F_md5(md5) #调用md5 hash1计算方法，并获取结果
    
    e1.delete(0, tk.END) #清空DATA输入框内的值
    e1.insert(0,md5) 

    e2.delete(0, tk.END) #清空Md516输入框内的值
    e2.insert(0,mh[0])   #将计算得到的Md516值放入框内
    e3.delete(0, tk.END) #清空md532输入框内的值
    e3.insert(0,mh[1])   #将计算得到的Md532值放入框内
    e4.delete(0, tk.END) #清空Hash输入框内的值
    e4.insert(0,mh[2])   #将计算得到的hash值放入框内
    
if __name__ == "__main__":
    master = tk.Tk()
    master.title("Md5 Sha1加密") #标题
    # 300x300代表了初始化时主窗口的大小，200，200代表了初始化时窗口所在的位置
    master.geometry('520x135+200+200')
    
    #创建三个DATA、MD5、Sha1标签，并以Grid方式布局。
    tk.Label(master, text="",width=10).grid(row=0,column=0)
    tk.Label(master, text="Data:",width=10).grid(row=1,column=0)
    tk.Label(master, text="MD516:",width=10).grid(row=2,column=0)
    tk.Label(master, text="MD532:",width=10).grid(row=3,column=0)
    tk.Label(master, text="Sha1:",width=10).grid(row=4,column=0)

    #创建三个DATA、MD5、Sha1输入框，并以Grid方式布局。
    e1 = tk.Entry(master,width=50)
    e2 = tk.Entry(master,width=50,state = 'normal')
    e3 = tk.Entry(master,width=50,state = 'normal')
    e4 = tk.Entry(master,width=50,state = 'normal')
    e1.grid(row=1, column=1)
    e2.grid(row=2, column=1)
    e3.grid(row=3, column=1)
    e4.grid(row=4, column=1)
    
    #创建“START”按钮，并以Grid方式布局。
    b1=tk.Button(master,text = 'Start',width=10,command = view_md5)
    b1.grid(row=1,column=3,rowspan=4)
```
