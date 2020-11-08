# 《深入理解Spring MVC源代码：从原理分析到实战应用》图书勘误

1. 367： 可以发现3个过滤条件以前 -> 可以发现3个过滤条件之间
2. 385：省略rome库相关转化器判断与添加逻辑 -> 不知道是啥。看了下源码，没有问题，省略的是：
```
private static boolean romePresent =
		ClassUtils.isPresent("com.rometools.rome.feed.WireFeed",
				WebMvcConfigurationSupport.class.getClassLoader());
		if (romePresent) {
	messageConverters.add(new AtomFeedHttpMessageConverter());
	messageConverters.add(new RssChannelHttpMessageConverter());
}
```
3. 跨域请求的处理源码分析没有写
4. 145：这些属性值都是按照固定的结果通过配置文件配置的 -> 这些属性值都是按照固定的结构通过配置文件配置的
5. 65：最后再补充一个比较特殊的路径模式，该例子来自Spring MVC的官方文档：对于请求路径为/spring-web-3.0.5.jar，使用如下path：。后面的示例代码错误，应为
```
@GetMapping("/{name:[a-z-]+}-{version:\\d\\.\\d\\.\\d}{ext:\\.[a-z]+}")
public void handle(@PathVariable String name, @PathVariable String version, @PathVariable String ext) {
    // ...
}
```
6. 84：在逻辑上与@RequestBody是互逆的，@RequestBody是把请求体反序列化为指定类型的对象，而@RequestBody则是把指定类型的对象序列化为响应体返回给客户端。 -> 在逻辑上与@RequestBody是互逆的，@RequestBody是把请求体反序列化为指定类型的对象，而@ResponseBody则是把指定类型的对象序列化为响应体返回给客户端。
7. 109：不会关系其请求与响应 -> 不会关心其请求与响应
8. 218：（2）获取请求处理器。（3）查找处理适配器 -> （2）查找请求处理器。（3）获取处理适配器
9. 222：则直接返回状态码304，表示服务端为对此资源进行修改 -> 则直接返回状态码304，表示服务端未对此资源进行修改
10. 41: 在项目中引入spring-boot-starter-freemarker依赖后，Spring Boot的自动配置机制就会生效，自动生成ThymeleafViewResolver到Spring MVC中 -> 在项目中引入spring-boot-starter-thymeleaf依赖后，Spring Boot的自动配置机制就会生效，自动生成ThymeleafViewResolver到Spring MVC中

致谢：
jiangnan520025：5、6、7、8、9
