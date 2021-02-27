# AddressBook（通信录）
背景：添加联系人的电话和姓名，用户可以进行编辑更改和删除等基本功能
# 可实现功能
可以进行联系人的姓名和电话的添加、编辑和删除功能，实现自动登录和注销功能
# 使用方法
1.输入正确的账号和密码。账号；123456 密码：123456 如果账号密码正确则可以进入主界面，反之则会提醒密码错误进入另一界面。
2.进入主界面之后点击右上角的“+”即可添加新的联系人的相关信息。如需更改编辑只需点击对应的cell，进入界面后在点击右上角“编辑”即可进行编辑
3.如果想要删除联系人只需左滑即可删除目标联系人。
4.如若想要退出登录，点击左上角“注销”按钮即可注销
# APP构成板块，开发思路
App主要由TableViewController和数个ViewController以及一个NavigationController通过系列的逻辑判断，文本监听，按钮的点击事件等相关逻辑操作构成。
# 所使用的技术和知识点
1.在登录界面所使用的重要技术就是实时监听两个TextField的文本框，因为其和UIButton一样，继承的是UIControll所以我们采用AddTarget的方法来进行监听。同时通过判断账号密码的正误来选择页面的跳转，由于要判断密码的正误，所以我们设置的是一个手动型的segue来进行页面跳转，所用的方法是performSegueWithIdentifier来进行指定跳转。                                                          
2.进入主页面之后，首先大体上是一个UITableViewController作为主体，由于ActionSheet方法过期，所以我们采用AlertController来进行“注销”和“+”这两个按钮的设置
3.进入添加联系人界面后，就只有一些Label、TextField和Button基础按钮，此时的Button--“添加”只要点击都会保存并pop回上一个界面，所以我们采用自动型的segue，我们创建了数组，设置了cell的内容并让其显示，因为要将我们添加的内容显示在主界面中，所以还涉及到了逆传的内容，添加了联系人的代理方式将数据放在我们命名的Contacts数组中来进行逆传，除此之外为了返回主界面后我们再次点击cell能够跳转到编辑界面，我们获取了cell的位置即indexpath，设置了了代理edit.delegate = self 进行了顺传赋值
5.如果想要对已添加的联系人进行编辑修改点击cell再点击右上角的“编辑”按钮即可进行编辑，由于未点击编辑时文本框不可改动所以所以还设置了相关enabled属性来开启或关闭
6.因为会保存所以有应用沙盒以及解档、归档的内容，写了解档、归档的属性和所遵守的协议
7.删除联系人用到了TableView自己的一个编辑模式来进行删除
# 心得体会
这次考核自己还是很用心的在做，可能自身基本功不是很扎实，语法知识懂得不多，问了很多学长，看了书本《七天玩转ios界面开发》和B站小码哥、黑马程序员的视频以及一些博客内容。开始的时候还是很艰难的，在代码和StoryBoard中反复横跳，但是做了这个作业过后，真的自己收获的不是一星半点儿。App本身的内容、操作和所实现的功能并不多，但是自己明白了页面之间的相互联系、跳转、一些简单功能的实现方法。最后，真的真的非常感谢学长们的帮助，是你们给帮我纠正Bug，给我看了一些方法实现的Demo，和我通话为我阐明一些基础语法内容，谢谢！希望自己在后续的学习过程中能将已学知识掌握得更加牢靠，并努力学习新的知识！
