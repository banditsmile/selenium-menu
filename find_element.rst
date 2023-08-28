查找元素
===================
对于操作浏览器中的页面的自动化测试框架来说，肯定少不了 去发现网页中的元素，你只有发现那些元素实时存在了才能做出下一步的操作。Selenium中提供了众多的方法供我们去找到网页中的元素，这给我们带来了很大的便利，那么都有哪些方法了，我们可以通过Python快速获取到这些方法：

===================================  =============================================
find_element                         #通过指定方法查找指定的一个元素(需指定两个参数)
find_element_by_class_name           #通过Class name查找指定的一个元素
find_element_by_css_selector         #通过CSS选择器查找指定的一个元素
find_element_by_id                   #通过ID查找指定的一个元素
find_element_by_link_text            #通过链接文本获取指定的一个超链接(精确匹配)
find_element_by_name                 #通过Name查找指定的一个元素
find_element_by_partial_link_text    #通过链接文本获取指定的一个超链接(模糊匹配)
find_element_by_tag_name             #通过标签名查找指定的一个元素
find_element_by_xpath                #通过Xpath语法来指定的一个元素
find_elements                        #通过指定方法查找所有元素(需指定两个参数)
find_elements_by_class_name          #通过Class name查找所有元素
find_elements_by_css_selector        #通过CSS选择器查找所有元素
find_elements_by_id                  #通过ID查找所有元素
find_elements_by_link_text           #通过链接文本获取所有超链接(精确匹配)
find_elements_by_name                #通过Name查找所有元素
find_elements_by_partial_link_text   #通过链接文本获取所有超链接(模糊匹配)
find_elements_by_tag_name            #通过标签名查找所有元素
find_elements_by_xpath               #通过Xpath语法来查找所有元素
===================================  =============================================

可以看到输入框的ID为KW，Name为WD，这里我们选择ID，选择ID有三种方法，如下：

.. code-block:: python
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.get('https://www.baidu.com')
    kw1=c.find_element(By.ID,'kw')
    kw2=c.find_element_by_id('kw')
    kw3=c.find_elements_by_id('kw')[0]
    print(kw1)
    print(kw2)
    print(kw3)


可以看到我们成功使用三种方法获取到了这个元素，其它方法差不多，都是一通百通，喜欢哪种方法就使用哪种方法。

