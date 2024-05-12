---
layout: post
title: MyBatisPlus分页
---
在MyBatis-Plus中，自定义SQL分页可以通过使用Page类和自定义的Mapper方法实现。以下是一个简单的例子：

通过配置类来指定一个具体数据库的分页插件，因为不同的数据库的方言不同，具体生成的分页语句也会不同，这里我们指定数据库为Mysql数据库
```
@Configuration
public class MybatisPlusConfig {
    @Bean
    public MybatisPlusInterceptor mybatisPlusInterceptor() {
        MybatisPlusInterceptor interceptor = new MybatisPlusInterceptor();
        interceptor.addInnerInterceptor(new PaginationInnerInterceptor(DbType.MYSQL));
        return interceptor;
    }
}
```

首先，在Mapper接口中定义一个方法，该方法接收Page对象和其他查询参数：

```
public interface CustomMapper extends BaseMapper<Entity> {
    IPage<Entity> selectCustomPage(Page<Entity> page, @Param("param") CustomQueryParam param);
}
```

然后，在Mapper XML中定义对应的SQL语句，并使用MyBatis-Plus提供的分页语法：

```
<select id="selectCustomPage" resultType="Entity">
    SELECT * FROM some_table
    WHERE some_condition = #{param.someField}
    <!-- 使用MyBatis-Plus提供的分页语法 -->
    <if test="page != null">
        LIMIT #{page.offset}, #{page.size}
    </if>
</select>
```

最后，在服务层调用这个方法：

```
@Service
public class CustomService {
 
    @Resource
    private CustomMapper customMapper;
 
    public IPage<Entity> getCustomPage(Page<Entity> page, CustomQueryParam param) {
        return customMapper.selectCustomPage(page, param);
    }
}
```

最后进行测试
```
@Autowired
private CustomService customService;

@Test
public void testSelectPageVo(){
    //设置分页参数
    Page<Entity> page = new Page<>(current, size);
    customService.getCustomPage(page, param);
    //获取分页数据
    List<Entity> list = page.getRecords();
    list.forEach(System.out::println);
    System.out.println("当前页："+page.getCurrent());
    System.out.println("每页显示的条数："+page.getSize());
    System.out.println("总记录数："+page.getTotal());
    System.out.println("总页数："+page.getPages());
    System.out.println("是否有上一页："+page.hasPrevious());
    System.out.println("是否有下一页："+page.hasNext());
}
```
