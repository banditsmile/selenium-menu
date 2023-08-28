选项操作
===================
我们可以通过给当前操作的对象一些选项来增强交互能力，如下：

.. code-block:: python
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    import time
    from selenium.webdriver.chrome.options import Options
    o=Options()
    o.add_argument('--headless')#无界面浏览
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe',chrome_options=o)
    c.get('https://www.baidu.com')
    kw1=c.find_element(By.ID,'kw')
    print(c.title)
    time.sleep(3)
    c.close()
    c.quit()


这个时候就实现了咱们的无界面浏览了，也就是不用打开浏览器即可自动返回执行的结果。不过你可别以为选项就那么一两个，那可是多到你怀疑人生的，例如：

.. code-block:: python
    o.add_argument('--window-size=600,600') #设置窗口大小
    o.add_argument('--incognito') #无痕模式
    o.add_argument('--disable-infobars') #去掉chrome正受到自动测试软件的控制的提示
    o.add_argument('user-agent="XXXX"') #添加请求头
    o.add_argument("--proxy-server=http://200.130.123.43:3456")#代理服务器访问
    o.add_experimental_option('excludeSwitches', ['enable-automation'])#开发者模式
    o.add_experimental_option("prefs",{"profile.managed_default_content_settings.images": 2})#禁止加载图片
    o.add_experimental_option('prefs',
    {'profile.default_content_setting_values':{'notifications':2}}) #禁用浏览器弹窗
    o.add_argument('blink-settings=imagesEnabled=false')  #禁止加载图片
    o.add_argument('lang=zh_CN.UTF-8') #设置默认编码为utf-8
    o.add_extension(create_proxyauth_extension(
               proxy_host='host',
               proxy_port='port',
               proxy_username="username",
               proxy_password="password"
           ))# 设置有账号密码的代理
    o.add_argument('--disable-gpu')  # 这个属性可以规避谷歌的部分bug
    o.add_argument('--disable-javascript')  # 禁用javascript
    o.add_argument('--hide-scrollbars')  # 隐藏滚动条
    o.binary_location=r"C:\Users\Administrator\AppData\Local\Google\Chrome\Application" #指定浏览器位置
    o.add_argument('--no-sandbox')  #解决DevToolsActivePort文件不存在的报错

其实选项的添加无非就是分为以下这几种，如下：

.. code-block:: python
    o.set_headless()          #设置启动无界面化
    o.binary_location(value)  #设置chrome二进制文件位置
    o.add_argument(arg)               #添加启动参数
    o.add_extension(path)                #添加指定路径下的扩展应用
    o.add_encoded_extension(base64)      #添加经过Base64编码的扩展应用
    o.add_experimental_option(name,value)         #添加实验性质的选项
    o.debugger_address(value)                #设置调试器地址
    o.to_capabilities()                    #获取当前浏览器的所有信息

虽然选项很多，但是我们真正能用到的不多，一般就是无痕模式或者禁用JavaScript和图片来快速获取到相关信息。虽然我们上面使用的是Options方法，但是在实际应用中建议大家使用的ChromeOptions方法。

