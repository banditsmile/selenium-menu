元素操作
===================

对我们找到的元素进行二次操作，不仅可以再次选择子元素还可以进行其它操作。如下：

======================================  ======================================
kw1.clear()                             #清除元素的值
kw1.click()                             #点击元素
kw1.id                                  #Selenium所使用的内部ID
kw1.get_property('background')          #获取元素的属性的值
kw1.get_attribute('id')                 #获取元素的属性的值
kw1.location                            #不滚动获取元素的坐标
kw1.location_once_scrolled_into_view    #不滚动且底部对齐并获取元素的坐标
kw1.parent                              #父元素
kw1.send_keys('')                       #向元素内输入值
kw1.size                                #大小
kw1.submit                              #提交
kw1.screenshot('2.png')                 #截取元素形状并保存为图片
kw1.tag_name                            #标签名
kw1.text                                #内容，如果是表单元素则无法获取
kw1.is_selected()                       #判断元素是否被选中
kw1.is_enabled()                        #判断元素是否可编辑
kw1.is_displayed                        #判断元素是否显示
kw1.value_of_css_property('color')      #获取元素属性的值
kw1._upload('2.png')                    #上传文件
======================================  ======================================

