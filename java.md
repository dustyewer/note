application.properties中文乱码是因为spring boot默认加载的是ISO-8859-1字符集
可以让idea显示为为中文，实际还是ISO-8859-1
或者使用UTF8格式的文件，但是需要在使用时指定字符集
@PropertySource(value="classpath:test.properties",encoding="UTF-8")
@Value("${test.cn}")
String testCn;

@NotBlank 不要用在非字符串上

Mybatis映射文件的sql语句默认不支持以";"结尾，也就是不支持多sql语句。需要在mysql的url 后面加上 &allowMultiQueries=true

mysql 存储过程不会自动开启事物

#spring 启动后动作
CommandLineRUnner

SmartLifeCycle

启动前 @PostConsturct 销毁前 @PreDestroy

@ControllerAdvice 统一异常处理

System.getProperty(line.separator) 跨平台的换行

StringBuilder 后出的，不安全，但快

spring的定时任务 默认单线程 @Async 可以简单的开启多线程

#后端跨域 的4种方法
1.实现WebMvcConfigurer
2@CrossOrigin
3实现Filter
4配置类 WebMcvConfigurerAdapter

@ServletComponentScan
使@WebServlet @WebFilter @WebListener 标记的 Servlet Filter Listener 自动注册到Servlet容器中，无需其他代码
而起不能再加@Component注解，否则urlPatterns 失效