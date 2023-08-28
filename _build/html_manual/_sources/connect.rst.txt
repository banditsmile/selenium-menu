与浏览器建立连接
===================
做好前面的准备工作，我们只需要写入几行Python代码即可与浏览器进行交互，如下：

::

    from selenium import webdriver
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe') #获取chrome浏览器的驱动，并启动Chrome浏览器
    c.get('https://www.baidu.com')#打开百度
