# Markdown语法简记

# 标题一

## 标题二

## 文本样式

**加粗** 

*斜体* 

***斜体加粗*** 

~~删除线~~ 

## 引用文本
>大家好，我是一个引用文本！

## 代码

我需要在文本中插入快捷键 `ctrl + v`

我需要引用一段代码：
```java
public class CurrentTime {
	private Date date;
	private String dateString;

	public CurrentTime() {
		date = new Date();
		SimpleDateFormat format = new SimpleDateFormat("yyyy-MM-dd HH:mm");
		dateString = format.format(date);
	}

	public String getDateString() {
		return dateString;
	}
}
```

## 链接
[链接到百度](https://www.baidu.com/)

[链接到我的服务器][myServer]

[链接到表情库][emoji]

[myServer]:http://47.107.160.68/

[emoji]:https://www.webfx.com/tools/emoji-cheat-sheet/

## 列表
- 主列表1
* 主列表2
  1. 次列表1
  2. 次列表2
+ 主列表3

## 任务列表

- [x] 任务列表1(已完成)
- [ ] 任务列表2(未完成)

## 表情
  **[链接到表情库][emoji]**
  
  表情1: :musical_keyboard:
  
  表情2： :game_die:
  
  ## 注释
  \*\* 对关键字\*的注释方式
  
  ## 图片
  
  + 网络图片
  
  	![网络图片](http://image.baidu.com/search/detail?ct=503316480&z=undefined&tn=baiduimagedetail&ipn=d&word=%E9%A3%8E%E6%99%AF%E5%9B%BE%E7%89%87&step_word=&ie=utf-8&in=&cl=2&lm=-1&st=undefined&hd=undefined&latest=undefined&copyright=undefined&cs=3799560630,1610896717&os=82062887,1653182010&simid=4236875329,698766527&pn=15&rn=1&di=34130240760&ln=1737&fr=&fmq=1546243912461_R&fm=&ic=undefined&s=undefined&se=&sme=&tab=0&width=undefined&height=undefined&face=undefined&is=0,0&istype=0&ist=&jit=&bdtype=0&spn=0&pi=0&gsm=0&hs=2&objurl=http%3A%2F%2Fpic9.photophoto.cn%2F20081229%2F0034034829945374_b.jpg&rpstart=0&rpnum=0&adpicid=0&force=undefined)
	

  + 把图片存入markdown
     请参考 [这个链接](https://www.zhihu.com/question/21065229)
  






















