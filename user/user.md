# 1，maven 官方仓库查找

## 1.1 复制maven 的坐标 

```
<dependency>
  <groupId>com.github.ducheng</groupId>
  <artifactId>dynamic-redis-spring-boot-starter</artifactId>
  <version>0.0.2</version>
</dependency>
```



## 1.2 在配置文件配置多数据源

```properties
# 是否开启多数据源
spring.redis.enable-multi=true
spring.redis.multi.default.host=你的ip
spring.redis.multi.default.host.password="你的密码"
spring.redis.multi.default.port=你的端口
spring.redis.multi.test.host=你的ip
spring.redis.multi.test.port=你的端口
spring.redis.multi.test.host.password="你的密码" 这里的test 就是数据源的名称
```

# 1.3  使用案例

## 1.3.1  之前的springboot 整合redis 应该怎么配置就怎么配置，这里只演示使用注解的方式

## 1.3.2 代码片段

```java

	@Autowired
	RedisTemplate redisTemplate;

	@GetMapping("/test")
	@RdbSelect(dataSource = "test", db = 10)
	public String test() {
		redisTemplate.opsForValue().set("k1","v1");
		return "test";
	}

```

