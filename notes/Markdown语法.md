
# Markdown语法简记

## 1.标题
emsp;语法：`#` 的个数代表标题级别。

## 2.文本样式

`**加粗**` emsp; **加粗** 

`*斜体*` emsp; *斜体* 

`***斜体加粗*** ` emsp; ***斜体加粗*** 

`~~删除线~~ ` emsp; ~~删除线~~ 

### 引用文本

`>引用文本`

>大家好，我是一个引用文本！

## 3.代码

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

## 4.链接
emsp;语法：`[显示的文字](url)`

[链接到百度](https://www.baidu.com/)

[链接到我的服务器][myServer]

[链接到表情库][emoji]

[myServer]:http://47.107.160.68/

[emoji]:https://www.webfx.com/tools/emoji-cheat-sheet/

## 5.列表
emsp;语法： `* + -`均可。 

- 主列表1
* 主列表2
  1. 次列表1
  2. 次列表2
+ 主列表3

### 任务列表
emsp;语法：  `- [x] 或者 - [ ]`

- [x] 任务列表1(已完成)
- [ ] 任务列表2(未完成)

## 6.表情
  **[链接到表情库][emoji]**
  
  测试表情1: :musical_keyboard:
  
  测试表情2： :game_die:
  
## 7.注释
  用 `\`对关键字的注释！
  
## 8.图片

  + 网络图片 &emsp; 语法： `![test](url)`
  	![网络图片](https://github.com/magentaLi/My-CS-Notes/blob/master/pictures/pxyz.jpg"蜘蛛侠之平行宇宙")
  + 把图片存入markdown
     请参考 [这个链接](https://www.zhihu.com/question/21065229)
  
## 9.缩进
`&ensp;`半角缩进
`&emsp;`全角缩进












