=====================
框架操作(Frame/IFrame)
=====================

我们还可以操作框架里的东西，比如IFrame，Frame等等，虽然都是框架，但是这两者操作起来还是有很大差别的。下面我们就来看看吧，如下：

 .. code-block:: python
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    import time
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.implicitly_wait(10)
    c.get('https://hao.360.com/?a1004')
    #ss=c.find_element(By.CLASS_NAME,'NEWS_FEED_VIDEO_1595850774217HPA70')#不容易找到标签
    c.switch_to.frame(0)#索引
    c.switch_to.frame('NEWS_FEED_VIDEO_1595850774217HPA70-VideoIframe') #ID
    c.switch_to.frame('NEWS_FEED_VIDEO_1595850774217HPA70')#Class
    c.switch_to.frame(c.find_element_by_tag_name("iframe"))#标签
    time.sleep(3)
    c.close()
    c.quit()

这里小编是以360浏览器的主页为例子，对它里面的IFrame进行访问，最有效的方法一般就是我上面提到的四种了。这里我们有时候因为这个框架需要加载才可以出来，所以很多时候是无法获取到的，因此我们只有使用滑动加载到出现这个标签或者ID，Class为可以获取到，这在刚才小编是说了的，大家可以往前看看，不过这个方法不推荐使用，为啥？因为开发者文档上是这样写的。我们的Frame由于是IFrame里的子集，所以上面的方法便是可以层层遍历的好方法，但是如果我们遍历到最后了如何返回主框架了，可以这样做，如下所示：

.. code-block:: python
    c.switch_to.default_content()

这样就可以回到主框架继续进行操作了。如果我们由里往外遍历的话，那么可以这样来做，如下：

.. code-block:: python
    c.switch_to.parent_frame()

