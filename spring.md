@Autowired与@resource区别。
@resource>@Autowired 
一般@Autowired注入接口，@resource接口，类都行；因为@Autowired是根据类型去查找bean的，Resource是根据类型和名字

Spring不但支持自己定义的@Autowired注解，还支持JSR-250规范定义的几个注解。如：@Resource、@PostConstruct及@PreDestroy。

1. @Autowired
由spring提供，只按照byType注入

2. @Resource
由J2EE提供，默认是按照byName自动注入
---------------------------------------
@Resource有两个重要的属性，name和type：
Spring将@Resource注解的name属性解析为bean的名字，type属性则解析为bean的类型。
所以如果使用name属性，则使用byName的自动注入策略；而使用type属性则使用byType自动注入策略；
如果既不指定name也不指定type属性，这时通过反射机制使用byName自动注入策略。
-------------------------------------------------------------

@Resource装配的顺序：
如果同时指定了name和type属性，则从spring上下问中找到唯一匹配的bean进行装配，如果没有找到，则会抛出异常。
如果指定了name属性，则从spring上下文中查找名称（id）匹配的bean进行装配，找不到则抛出异常。
如果指定type属性，则从spring上下文中找到类型匹配的唯一bean进行装配，找不到或者是找到多个，则抛出异常。
如果既没有指定name属性，也没有指定type属性，则默认是按照byName的方式进行装配；如果没有匹配，则返回一个原始的类型进行装配，如果匹配则自动装配。
@Resource的作用是相当于@Autowired，只不过@Autowired是按照byType进行装配。
--------------------- 
. 使用区别
@Resource和@Autowired都可以用来装配bean，都可以写在字段上或者是写在setter方法上。
@Autowired默认是按照byType进行装配的，所以默认情况下是必须依赖的对象存在，如果要允许为空，可以设置它的required属性为false，如果想使用byName进行装配，可以结合@Qualifier注解进行使用。
@Resource默认是按照byName进行装配的，名称可以通过name属性进行制定，如果没有指定name属性，注解写在字段上时，默认是取字段名作为名称进行查找。如果注解写在setter方法上则默认是取属性的名称进行装配，当找不到与名称匹配的bean时才按照类型进行装配。但是值得注意的是，一旦指定了name属性，就会按照名称进行装配。
推荐使用@Resource注解在字段上，这样就不需要写setter方法了，并且这个属性是属于J2EE的，从而可以减少对spring的耦合
--------------------- 

spring配置了包扫描方式(springmvc.xml)，但是依然扫描不到包？

父项目打包成war包，Pom文件没有配置子项目(即pom文件中依赖的子项目没有添加)。

spring接口service注入失败？
接口没有实现当然失败。


