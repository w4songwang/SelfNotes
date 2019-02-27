### MarkDown
- [马克飞象 MarkDown在线编辑](https://maxiang.io/)
- [语法](https://blog.csdn.net/witnessai1/article/details/52551362)
- [编辑器推荐](http://www.williamlong.info/archives/4319.html)




### 字符串MD5加密成guid
``` c#
public static Guid EncryptWithMD5(string source)
{
    byte[] sor = Encoding.UTF8.GetBytes(source);
    MD5 md5 = MD5.Create();
    byte[] result = md5.ComputeHash(sor);
    return new Guid(result);
}
``` 


### SQLServer字符串MD5加密成guid
``` sql
select cast(HASHBYTES('MD5','HG8001') as uniqueidentifier)
```

### [sql 日志文件过大怎么清除](https://jingyan.baidu.com/article/d2b1d102cffb8b5c7e37d4a4.html)
``` sql
--SQL 2008收缩清空日志方法：1.在SQL2008中清除日志就必须在简单模式下进行，等清除动作完毕再调回到完整模式，一定必务要再改回完整模式，不然数据库就不支持时间点备份了。1).选择数据库–属性—选项—恢复模式–选择简单。2).收缩数据库后，再调回完整。2.可以用命令直接操作
[sql] view plain copy
USE[master]  
GO  
ALTER DATABASE 要清理的数据库名称 SET RECOVERY SIMPLE WITH NO_WAIT  
GO  
ALTER DATABASE 要清理的数据库名称 SET RECOVERY SIMPLE   --简单模式  
GO  
USE 要清理的数据库名称  
GO  
DBCC SHRINKFILE (N'要清理的数据库名称_log' , 2, TRUNCATEONLY)  --设置压缩后的日志大小为2M，可以自行指定  
GO  
USE[master]  
GO  
ALTER DATABASE 要清理的数据库名称 SET RECOVERY FULL WITH NO_WAIT  
GO  
ALTER DATABASE 要清理的数据库名称 SET RECOVERY FULL  --还原为完全模式  
GO  
```


### [SQL Server：查看SQL日志文件大小命令](https://www.cnblogs.com/hongb/p/5113474.html)


### 数据库数据同步
``` sql
	--更新操作=删除旧数据+插入最新数据
	alter table HtcTroubleSupervises  NOCHECK constraint all; 

	select * into #tmp from
	[172.48.1.195].carihtc.dbo.HtcTroubleSupervises

	insert into HtcTroubleSupervises
	select * from #tmp
	where #tmp.id not in (select id from HtcTroubleSupervises)

	drop table #tmp

	alter table HtcTroubleSupervises  CHECK constraint all; 
```



### 前端学习网站
- [Web Platform Docs](https://webplatform.github.io/)
- [Mozilla Developer Network ](https://developer.mozilla.org/zh-CN/)


### Ionic相关网站
- [【组件篇】ionic3开源组件](https://www.jianshu.com/p/3e156999eaa4)



### 工具类网站
- [Red Gate系列文章](https://www.cnblogs.com/VAllen/archive/2012/09/27/SQLDataCompare.html)
- [SwitchHosts](https://github.com/oldj/SwitchHosts/blob/master/README_cn.md)

### docs.microsoft.com 文档
- [NuGet 文档](https://docs.microsoft.com/zh-cn/nuget/)


### 优秀博客
- [鱼东东 - 博客园](https://www.cnblogs.com/yudongdong/)
- [dotNET跨平台](https://me.csdn.net/sD7O95O)
- [零度编程](https://www.xcode.me/)

### 陌生的概念
- [burpsuite、时序分析、QQ关系库](https://mp.weixin.qq.com/s?__biz=MzI0MDQ4MTM5NQ==&mid=2247488579&idx=1&sn=f0248519c5d33fd1598af8427e90dfc3&chksm=e91b715fde6cf849395e78cee4d8a2d74a2944fd3934cae8f929182b43b591c51ca8fd9cfb6c&mpshare=1&scene=23&srcid=0220JVhnq2eStE5trGO5HVfX#rd)
-数据库：同义词、sqlserver关闭约束
