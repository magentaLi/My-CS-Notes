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






















