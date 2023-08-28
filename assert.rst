判断
=======

在Selenium中我们在做自动化测试时常无法判断一个元素是否真的显示出来了，因此会各种报错，接下来我们对这些操作进行判断，如果显示出了我们预期的值，那么就进行下一步操作，否则就关闭或者暂停几秒然后再判断，这里我要跟大家说Selenium中的一个模块-----Expected_Conditions，简称为EC，如下所示：

.. code-block:: python
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    from selenium.webdriver.support import expected_conditions as EC
    import time
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.implicitly_wait(10)
    c.get('https://baidu.com')
    t=EC.title_is('百度一下，你就知道')
    print(t(c))
    time.sleep(3)
    c.close()
    c.quit()

这里其实就是判断当前页面的标题是否是我们给定的文本，可以看出这里为True，说明是。它不光就一个方法哦，还有其它的，小编在这里大致说下，如下所示：

.. code-block:: python
    EC.title_contains('')(c)#判断页面标题是否包含给定的字符串
    EC.presence_of_element_located('')(c) #判断某个元素是否加载到dom树里，该元素不一定可见
    EC.url_contains('')(c) #判断当前url是否包含给定的字符串
    EC.url_matches('')(c) #匹配URL
    EC.url_to_be('')(c)  #精确匹配
    EC.url_changes('')(c) #不完全匹配
    EC.visibility_of_element_located('')(c) #判断某个元素是否可见,可见代表元素非隐藏元素
    EC.visibility_of('')(c)   #跟上面一样，不过是直接传定位到的element
    EC.presence_of_all_elements_located('')(c) #判断是否至少有1个元素存在于dom树中
    EC.visibility_of_any_elements_located('')(c) #判断是否至少一个元素可见，返回列表
    EC.visibility_of_all_elements_located('')(c) #判断是否所有元素可见，返回列表
    EC.text_to_be_present_in_element('')(c) #判断元素中的text是否包含了预期的字符串
    EC.text_to_be_present_in_element_value('')(c)#判断元素中value属性是否包含预期的字符串
    EC.frame_to_be_available_and_switch_to_it('')(c) # 判断该frame是否可以switch进去
    EC.invisibility_of_element_located('')(c) #判断某个元素是否不存在于dom树或不可见
    EC.element_to_be_clickable('')(c) #判断某个元素中是否可见并且可点击
    EC.staleness_of('')(c)  #等某个元素从dom树中移除
    EC.element_to_be_selected('')(c)  #判断某个元素是否被选中了,一般用在下拉列表
    EC.element_located_to_be_selected('')(c) #判断元组中的元素是否被选中
    EC.element_selection_state_to_be('')(c) #判断某个元素的选中状态是否符合预期
    EC.element_located_selection_state_to_be('')(c) #跟上面一样，只不过是传入located
    EC.number_of_windows_to_be('')(c)  #判断窗口中的数字是否符合预期
    EC.new_window_is_opened('')(c)  #判断新的窗口是否打开
    EC.alert_is_present('')(c)  #判断页面上是否存在alert

这就是它全部的方法了，简直不要多简单。