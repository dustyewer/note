new String(prop.getProperty(key).getBytes("Latin1"),"GBK")
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

#统一异常处理
@ControllerAdvice 

#跨平台的换行
System.getProperty(line.separator) 

StringBuilder 后出的，不安全，但快

spring的定时任务 默认单线程 @Async+@EnableAsync可以简单的开启多线程,线程数量不可控，可以在@Async("xx")中指定特大线程池

#后端跨域 的4种方法
1.实现WebMvcConfigurer
2@CrossOrigin
3实现Filter
4配置类 WebMcvConfigurerAdapter

#@ServletComponentScan 注解
使@WebServlet @WebFilter @WebListener 标记的 Servlet Filter Listener 自动注册到Servlet容器中，无需其他代码
而起不能再加@Component注解，否则urlPatterns 失效

#X-Frame-Options 可以在apach里tomcat里nginx里IIS里HAProxy里配置，可以用alibaba.spring.websecurity.DefaultWebSecurityConfigurer配置
nginx里 add_header X-Frame-Options SAMEORIGIN;

#SQL注入
只要是用户输入的地方都要#{}，order by 只能用&{},有sql注入的风险，需要在代码里面保护，或则在xml里判断，限制为可能的选项

#隐藏ng版本
server_tokens off;

#ng限制refer
valid_referers none block server_name *.my.com.cn;
if($invalid_referer){
	return 403 "Forbidden Access";
}
none:请求报文首部没有referer 直接通过浏览器或其他工具访问
blocked: 请求报文有referer 但有无效值 可能是被代理服务器或防火墙屏蔽
server_names: referer中包含本主机名


#过滤器 适合处理 编解码 防盗链 ，跨域

#webFilter 的 urlPatterns失效
过滤器不要加@Component注解 只要@WebFilter

#子类重写父类方法要抛出和父类一致的异常，或则不抛出异常，不能超出父类的范畴

#mybatis中resultMap标签中的extends就和类的继承一样

#idea debug运行不起来可能是因为断点打到函数名上了

#maven
maven-jar-plugin  可执行jar包与依赖包是分开的，需要建立lib目录来存放所需的依赖包，且jar包与lib目录在同级别目录中
maven-assembly-plugin 所有的依赖包放入可执行jar包，但是该插件会缺失spring的xds文件，导致jar包无法运行，而且当同级别目录下还有其他可执行文件依赖可能会产生冲突
maven-shade-plugin 所有的依赖包放入可执行的jar包中，当同级别目录中有其他的可执行jar包时，依赖可能会产生冲突，且运行jar包时，有时候会出现类似SF，DSA，RSA文件冲突的提示

#SpringRunner 和 SpringJUnit4ClassRunner有什么区别
SpringRunner继承里SpringJUnit4ClassRunner，没有扩展任何功能，SpringJUnit4ClassRunner更像是JUnit和Spring Test的桥接适配器，在Spring环境下，一般使用SpringRunner作为测试基准类


#md5
MessageDigest md5=MessageDigest.getInstance("MD5")
md5.update(input.getBytes(StandardCharsets.UTF_8))
byte[] digest=md5.digest()
#sha 512
MessageDigest.getInstance("SHA-512").digest(input.getBytes(StandardCharsets.UTF_8))

#byte数组操作
System.arraycopy(Object src,int srcPos,Object dest,int destPos,int length)

#spring国际化 默认已经支持，文件放到resources目录下，message开头的就是资源文件，框架会自动取
MessageSource.getMessage()

#javax.crypto.AEADBadTagException: Tag mismatch
微服务名称修改，要同步修改加密相关配置，否则会出现以上问题

afterCompletion 渲染完视图之后处理，一般用于资源的清理工作

BeanValidationPostProcessor  对所有的Bean在初始化前/后进行校验

@Constraint //指定自定义的校验类（校验类实现ConstraintValidator接口）

#命令行参数
--server.port=9090

#执行Shell任务的两种方式
1.java.lang 下的Runtime类
2.java.lang 下的ProcsssBuilder类

#泛型数组
AClass<BClass>[] test;
test = (AClass<BClass>[]) Array.newInstance(AClass.class,10);



