键盘鼠标操作
------
模拟键盘输入和按键

.. code-block:: python
    from selenium.webdriver.common.keys import Keys
    c.find_element(By.ID,'kw').send_keys('python')#输出Python
    c.find_element(By.ID,'kw').send_keys(Keys.ENTER)#回车键
    c.find_element(By.ID,'kw').click()#点击


这里列举出了一个最简单的键盘输入和鼠标点击的例子，不过我们在Selenium中可以使用更为高逼格的操作，那么是什么了？当然是咱们的鼠标键盘监听事件来触发事件啦，而且它里面的方法的确也很多样化，满足小编日常的骚操作不在话下，如下所示：

.. code-block:: python
    click(on_element=None)                 #鼠标左键单击
    click_and_hold(on_element=None)        #单击鼠标左键，不松开
    context_click(on_element=None)         #单击鼠标右键
    double_click(on_element=None)          #双击鼠标左键
    drag_and_drop(source,target)           #拖拽到某个元素然后松开
    drag_and_drop_by_offset(source,xoffset,yoffset) #拖拽到某个坐标然后松开
    key_down(value,element=None)     #按下键盘上的某个键
    key_up(value, element=None)      #松开键盘上的某个键
    move_by_offset(xoffset, yoffset)  #鼠标从当前位置移动到某个坐标
    move_to_element(to_element)        #鼠标移动到某个元素
    move_to_element_with_offset(to_element, xoffset, yoffset) #移动到距某个元素（左上角坐标）多少距离的位置
    pause(seconds)                  #暂停所有输入(指定持续时间以秒为单位)
    perform()                       #执行所有操作
    reset_actions()                 #结束已经存在的操作并重置
    release(on_element=None)       #在某个元素位置松开鼠标左键
    send_keys(*keys_to_send)        #发送某个键或者输入文本到当前焦点的元素
    send_keys_to_element(element, *keys_to_send) #发送某个键到指定元素


以上就是咱们鼠标和键盘的全部操作了，小编将用一个例子带大家零基础入门。如下：

.. code-block:: python
    from selenium import webdriver
    from selenium.webdriver.common.by import By
    import time
    from selenium.webdriver.common.keys import Keys
    from selenium.webdriver.common.action_chains import ActionChains
    c=webdriver.Chrome(executable_path=r'C:\Users\Administrator\AppData\Local\Google\Chrome\Application\chromedriver.exe')
    c.get('https://www.baidu.com')
    a=ActionChains(c)
    kw1=c.find_element(By.ID,'kw')
    tj=c.find_element(By.ID,'su')
    tj.send_keys(Keys.CONTROL,'c') #复制
    a.drag_and_drop(kw1,tj).perform()#从输入框拖动到搜索按钮
    kw1.send_keys(Keys.CONTROL,'v')#粘贴
    tj.send_keys(Keys.ENTER)
    time.sleep(3)
    c.close()
    c.quit()

这里我们通过对事件的监控，进行复制和粘贴，这里涉及到一个组合键的知识，大家注意。

