浏览器操作
===================
1.获取本页面URL
----------------
 .. code-block:: python
    c.current_url

2.获取日志
----------------
 .. code-block:: python
    c.log_types  #获取当前日志类型
    c.get_log('browser')#浏览器操作日志
    c.get_log('driver') #设备日志
    c.get_log('client') #客户端日志
    c.get_log('server') #服务端日志


3.窗口操作
----------------
 .. code-block:: python
    c.maximize_window()#最大化
    c.fullscreen_window() #全屏
    c.minimize_window() #最小化
    c.get_window_position() #获取窗口的坐标
    c.get_window_rect()#获取窗口的大小和坐标
    c.get_window_size()#获取窗口的大小
    c.set_window_position(100,200)#设置窗口的坐标
    c.set_window_rect(100,200,32,50)    #设置窗口的大小和坐标
    c.set_window_size(400,600)#设置窗口的大小
    c.current_window_handle   #返回当前窗口的句柄
    c.window_handles         #返回当前会话中的所有窗口的句柄

4.设置延时
----------------
 .. code-block:: python
    c.set_script_timeout(5) #设置脚本延时五秒后执行
    c.set_page_load_timeout(5)#设置页面读取时间延时五秒

5.关闭
----------------
 .. code-block:: python
    c.close() #关闭当前标签页
    c.quit() #关闭浏览器并关闭驱动


6.打印网页源代码
----------------
 .. code-block:: python
    c.page_source


7.屏幕截图操作
----------------
 .. code-block:: python
    c.save_screenshot('1.png')#截图，只支持PNG格式
    c.get_screenshot_as_png() #获取当前窗口的截图作为二进制数据
    c.get_screenshot_as_base64() #获取当前窗口的截图作为base64编码的字符串


8.前进后退刷新
----------------
 .. code-block:: python
    c.forward() #前进
    c.back()  #后退
    c.refresh()#刷新


9.执行JS代码
----------------

在Selenium中也可以自定义JS代码并带到当前页面中去执行，如下：
 .. code-block:: python
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    import time
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.get('https://www.baidu.com')
    kw1=c.find_element(By.ID,'kw')
    c.execute_script("alert('hello')")
    time.sleep(3)
    c.quit()


这里我使用一个JS中的函数来执行屏幕提示的功能，成功被执行。

10.Cookies操作
----------------
 .. code-block:: python
    c.get_cookie('BAIDUID') #获取指定键的Cookies
    c.get_cookies()         #获取所有的Cookies
    for y in c.get_cookies():
       x=y
       if x.get('expiry'):
           x.pop('expiry')
       c.add_cookie(x) #添加Cookies
    c.delete_cookie('BAIDUID') #删除指定键的Cookies内容
    c.delete_all_cookies() #删除所有cookies

11.获取标题内容
----------------
 .. code-block:: python
    c.title


12.获取当前浏览器名
----------------
 .. code-block:: python
    c.name

13.全局超时时间
----------------

 .. code-block:: python
    c.implicitly_wait(5)
