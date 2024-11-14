因为目前在Android系统上，还没有完全可以替代iOS手机的快捷指令的应用，即使是有类似的功能，要么就是收费的，要么无法完美实现自动化，比如像IFTTT，之前是可以免费使用，但是现在需要PRO版才行，因为这点小事去购买pro版我觉的不值得！
![](https://www.freedidi.com/wp-content/uploads/2024/10/20241019195219426-photo_2024-10-19_19-51-29-248x550.webp)
但是我们可以使用Zapier同样也可以创建自动化脚本，而且是完全免费的， 【[点击前往](https://zapier.com/)】注册账户

GV保号原理
Google Voice在收到手机号码新信息时，会向gmail发送一封通知邮件，如果发送者的号码不是5位数字的短码，信中会包含一句话：要回复此短信，请回复此电子邮件或访问 Google Voice。这句话可能因账号语言不同而有变化：
![](https://www.freedidi.com/wp-content/uploads/2024/10/195920-.png)
仔细看，这个发件人是双方的电话号码，经测试，发送邮件到这个地址等于用google voice回复短信。所以我们要做的就是发送定时邮件到这个地址。

需要好发件地址。地址一定要是这种格式：你的手机号.对方手机号.乱码@txt.voice.google.com

如果你没有的话，可以在手机随便找个APP用你的Google Voice注册一下。注意一定要手机号发来的验证码，如果是5位短码发的短信是不能邮件回复的。

拿到地址之后用Google账号登录Zapier，然后点击左上方的create 按钮
![](https://www.freedidi.com/wp-content/uploads/2024/10/20241019195645974-2024-10-19-195527-239x550.webp)
接着在create zap那里填
```
send gmail every month
```
AI会帮你选好所有脚本，直接点try it就行
![](https://www.freedidi.com/wp-content/uploads/2024/10/195920-1-1.png)
进去之后点第一个，右侧栏设置好每个月几号几点，test一下全变绿色对勾就行，然后下一步
![](https://www.freedidi.com/wp-content/uploads/2024/10/195921-.png)
第二步里，先点connect gmail旁边那个sign in，连接你要保号的那个谷歌账号，然后Action这里，To就填你拿到的邮箱地址，From选你的账号，Subject里写Re:，Body里填你想发送的短信内容（不要太长，也不要太短，太短容易被判定垃圾信息）。其他全部默认
![](https://www.freedidi.com/wp-content/uploads/2024/10/195921-1-1.png)
填完之后点continue，再test一下，然后去google voice看看有没有发送成功。
成功的话就可以点Publish发布。回到首页看看如果running这里是绿色的就完成了。
![](https://www.freedidi.com/wp-content/uploads/2024/10/195921-1-2.png)
最终的效果如下:
![](https://www.freedidi.com/wp-content/uploads/2024/10/195921-1-3.png)
