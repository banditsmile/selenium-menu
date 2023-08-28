显示等待和隐式等待
=====================

想必大家应该听过这个概念，显示等待就是浏览器在我们设置的时间内不断寻找，等到元素后才继续执行，如果没在规定时间内找到，也会抛异常；而隐式等待则是我们设置时间，然后程序去找元素，期间会不断刷新页面，到了时间仍然没找到就抛异常。这里有个常用的模块专门用来实现显示等待和隐式等待的，它就是”wait“,我们来看看吧。如下：

.. code-block:: python
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    import time
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.get('https://www.baidu.com/')
    su=WebDriverWait(c,10).until(lambda x:x.find_element_by_id('su'))
    su.location_once_scrolled_into_view
    print(su.get_attribute('value'))
    time.sleep(3)
    c.close()
    c.quit()

隐式等待很简单，就一行代码，如下：
.. code-block:: python
    c.implicitly_wait(10)

它的等待时间适用于全局的环境，也就是任何地方找不到某个元素，它都将发挥作用，如果找得到，则不会产生作用。