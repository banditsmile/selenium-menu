Alert
=======

在弹窗处理中，我们会遇到三种情况，如下：
 - 浏览器弹出框
 - 新窗口弹出框
 - 人为弹出框

那么我们该怎么分辨了？下面跟我一起看看吧。

1.浏览器弹出框
-----------
首先说说浏览器弹出框，想必大家对JavaScript中的Alert，Confirm，Prompt应该不是很陌生，就是弹出框，确认框，输入框；基本方法我们来看下，如下：

::

    from selenium.webdriver.common.alert import Alert
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.implicitly_wait(10)
    c.get('https://www.baidu.com')
    a1=Alert(c)
    a1.accept() #确定
    a1.dismiss() #取消
    a1.authenticate(username,password) #用户身份验证
    a1.send_keys('') #输入文本或按键
    a1.text  #获取弹窗内容

这里我们应对每种情况它上面的方法的对应位置都是会有所变化的，所以我们需要根据具体情况来进行操作，而且还可以使用另一种方法，如下：

::

    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.implicitly_wait(10)
    c.get('https://www.baidu.com')
    a1=c.switch_to_alert()
    a1.accept() #确定
    a1.dismiss() #取消
    a1.authenticate(username,password) #用户身份验证
    a1.send_keys('') #输入文本或按键
    a1.text  #获取弹窗内容

注：该类方法必须在有弹框的情况下才有作用，如没有会报错。

2.新窗口弹出框
-------------------

上面就是浏览器弹出框的处理方法了，如果是新窗口弹出的话那么就不一样了，我们需要通过句柄来定位，前面我们提到过这两个方法。下面我们来看看它们的具体用法，如下：

::

    from selenium import webdriver
    from selenium.webdriver.common.by import By
    import time
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.implicitly_wait(10)
    c.get('https://www.baidu.com')
    kw1=c.find_element(By.ID,'kw')
    tj=c.find_element(By.ID,'su')
    hwnd=c.window_handles #所有窗口句柄
    for h in hwnd:
       if h !=c.current_window_handle:  #如果句柄不是当前窗口句柄则切换                          c.switch_to_window(h)  #切换窗口
       else:
           print('无需切换窗口')
    time.sleep(3)
    c.close()
    c.quit()

注：如果有多个窗口，当你关闭了当前窗口想切换到另一个窗口，你需要把没关闭的窗口切换成当前活动窗口，因为Selenium是不会为你做这件事的。

3.人为弹出框
-------------------

这类弹出框是我们自己开发的，一般都是使用Div包裹一些其它的元素标签然后形成一个整体，当我们触发某个事件的时候就会出现，否则消失。这种弹出框使用我们的众多Find前缀的方法就能遍历到，很方便，这里不一一细说。