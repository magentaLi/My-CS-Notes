# Servlet 路径跳转相关的一些问题

  ## 在JSP页面访问servlet的方式：

  - **使用相对路径访问HelloServlet**:
  ```jsp
  <a href="servlet/HelloServlet">相对路径访问HelloServlet！</a>
  ```
  - **使用绝对路径方式访问HelloServlet**:
  ```java
  <a href="<%=request.getContextPath() %>/servlet/HelloServlet">绝对路径访问HelloServlet！</a>
  ```
  **表单中action的url地址写法与超链接方式完全相同**
  
  **xml 中的配置**:
  ```xml
    <servlet>
        <servlet-name>HelloServlet</servlet-name>
        <servlet-class>servlet.HelloServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>HelloServlet</servlet-name>
        <!--url-pattern必须已 / 开头，表示项目的根目录，采用注解的方式，urlPatterns 也应该以 / 开头-->
        <url-pattern>/servlet/HelloServlet</url-pattern>
    </servlet-mapping>
  ```
 ## 在servlet中进行跳转的方式：
 - 请求重定向的方式跳转到test.jsp 当前路径为ServletPathDirection/servlet/
 ```jsp
    //response.sendRedirect("test.jsp"); 此写法错误,下面正确
    //response.sendRedirect("../test.jsp");
    //或者使用 request.getContextPath() 获得上下文对象,下面的写法也正确
    response.sendRedirect(request.getContextPath() + "/test.jsp");
    
 ```
 - 服务器内部跳转的两种方式：（两种方式均正确)
 ```java
    //下面的 / 表示项目的根目录
    //request.getRequestDispatcher("/test.jsp").forward(request,response);
    //或者
    request.getRequestDispatcher("../test.jsp").forward(request, response);
 ```
 
 
 
  
