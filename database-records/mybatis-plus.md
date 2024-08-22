### mybatis-plus 随堂提问🙋

+ @TableName注解用于标记实体类，若实体类驼峰转下划线后与实际的数据库表名是一致的，其实没必要进行该注解的标记；
+ @TbaleId注解用于标记表中的主键，mybatis-plus会默认将实体类中叫id的属性当作数据库表的主键，若实际注解并非id，需要通过该注解进行标识
，且@TableId(value="user_id",type=IdType.AUTO)用于规定主键的自增规则
+ 哪几种情况会使用@TableFiled注解
    + 实体属性名与实际数据库字段名不一致的情况——@TableFiled("attch_type")
    + 实体属性名以is开头且是布尔类型，因为默认约定mp会将这种情况去掉is后作为字段名，那么就会出现实体变量名与实际数据库字段名不一致，那么就会报错——@TableFiled("is_use")
    + 实体属性不是表字段的，需要@TableFiled(exist = false)进行标识