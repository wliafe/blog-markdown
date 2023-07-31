# 常用数据库命令

```sql
#展示所有数据库
show databases;
#使用数据库
use ${databases_name};
#展示当前数据库所有表
shwo tables;
#展示表结构
desc ${table_name};
```

更多数据库命令，可以参考：[MySQL 有这一篇就够（呕心狂敲37k字，只为博君一点赞！！！）](https://blog.csdn.net/weixin_45851945/article/details/114287877)

# mysql数据库导入查询

```sql
#选择数据库
use ${database_name};
#导入数据（注意sql文件的路径）
source ${sql_path};
```

参考文章：[linux下导入、导出mysql数据库命令](https://blog.csdn.net/weixin_30299539/article/details/94830837)
