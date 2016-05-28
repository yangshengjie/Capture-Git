学习python一段时间了，爬两个网页练练手，该源代码是爬取韩寒博客的所有文章，并将文章链接下载到本地，关于将博客纯文字下载到本地见博主另外一篇文章：
# -*- coding: utf-8 -*-
import urllib
page=1
url = [' '] *350
i = 1
while page <=7:

    menu = "http://blog.sina.com.cn/s/articlelist_1191258123_0_"+str(page)+".html"
    print menu
    conn = urllib.urlopen(menu).read() #读取博客首页
    #print conn
    title = conn.find(r'<a title=')#找到文章标题
    href = conn.find(r'href=',title)#获取链接的开始序号，相对位置
    html = conn.find(r'.html',href)#获取链接的结束序号
    while i<= 320 and title != -1 and href != -1 and html != -1:
        url[i]= conn[href+6:html+5]#列表加减获取链接地址
        print "第"+str(i)+"篇文章的地址是：" +  url[i]
        file = url[i]   #下载文章
        content = urllib.urlopen(file).read()#读取该链接的文章内容
        filename = file[26:]
        print filename + "已下载"
        open(filename, 'w').write(content) #下载文章到本地，默认当前目录

        i  += 1
        title = conn.find(r'<a title' ,html)
        href = conn.find(r'href=',title)#获取链接的开始序号，相对位置
        html = conn.find(r'.html',href)#获取链接的结束序号
    page += 1
else:
    print "-------THE END!-----------"
