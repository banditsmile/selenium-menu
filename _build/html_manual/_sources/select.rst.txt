选择
=======

刚刚讲过判断，现在我们来说说选择，选择无非就是挑好的扔烂的，顺着思路来不会错，总体来讲还是挺简单的，如下：

::

    from selenium import webdriver
    from selenium.webdriver.common.by import By
    from selenium.webdriver.support import expected_conditions as EC
    from selenium.webdriver.support.select import Select
    import time
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.implicitly_wait(10)
    c.get('http://www.juliwz.cn/forum.php')
    s=Select(c.find_element_by_id('ls_fastloginfield'))#实例化
    res=s.all_selected_options#全部选中子项
    res1=s.options#全部子项
    print(res)
    print(res1)
    time.sleep(3)
    c.close()
    c.quit()

发觉主流网站都没有Select这个标签，于是找了个很冷门的网站，就一个Select。Select里面的方法也是相当多的，如下：

::

    s.first_selected_option  #第一个选中的子项
    s.select_by_index(index) #根据索引选择
    s.select_by_value(value)   #根据值来选择
    s.select_by_visible_text(text)  #根据选项可见文本
    s.deselect_by_index(index)   #根据索引来取消选择
    s.deselect_by_value(value)   #根据值来取消选择
    s.deselect_by_visible_text(text)  #根据可见文本来取消选择
    s.deselect_all()                #取消所有选择

这就是它全部的方法了，简直不要多简单。