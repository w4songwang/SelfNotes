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


### SQLServer 查看数据库各个表结构
``` sql
					  SELECT
     表名       = Case When A.colorder=1 Then D.name Else '' End,
     表说明     = Case When A.colorder=1 Then isnull(F.value,'') Else '' End,
     字段序号   = A.colorder,
     字段名     = A.name,
     字段说明   = isnull(G.[value],''),
     标识       = Case When COLUMNPROPERTY( A.id,A.name,'IsIdentity')=1 Then '√'Else '' End,
     主键       = Case When exists(SELECT 1 FROM sysobjects Where xtype='PK' and parent_obj=A.id and name in (
                      SELECT name FROM sysindexes WHERE indid in( SELECT indid FROM sysindexkeys WHERE id = A.id AND colid=A.colid))) then '√' else '' end,
     类型       = B.name,
     占用字节数 = A.Length,
     长度       = COLUMNPROPERTY(A.id,A.name,'PRECISION'),
     小数位数   = isnull(COLUMNPROPERTY(A.id,A.name,'Scale'),0),
     允许空     = Case When A.isnullable=1 Then '√'Else '' End,
     默认值     = isnull(E.Text,'')
 FROM
     syscolumns A
 Left Join
     systypes B
 On
     A.xusertype=B.xusertype
 Inner Join
     sysobjects D
 On
     A.id=D.id  and D.xtype='U' and  D.name<>'dtproperties'
 Left Join
     syscomments E
 on
     A.cdefault=E.id
 Left Join
 sys.extended_properties  G
 on
     A.id=G.major_id and A.colid=G.minor_id
 Left Join
 
 sys.extended_properties F
 On
     D.id=F.major_id and F.minor_id=0
 Order By
     A.id,A.colorder
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
``` sql
dbcc sqlperf(logspace)
```

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
- [microsoft-sysinternals](https://docs.microsoft.com/zh-cn/sysinternals/downloads/procdump)


### docs.microsoft.com 文档
- [NuGet 文档](https://docs.microsoft.com/zh-cn/nuget/)
- [零度编程](https://www.xcode.me/)


### 优秀博客
- [鱼东东 - 博客园](https://www.cnblogs.com/yudongdong/)
- [dotNET跨平台](https://me.csdn.net/sD7O95O)
- [零度编程](https://www.xcode.me/)

### 陌生的概念
- [burpsuite、时序分析、QQ关系库](https://mp.weixin.qq.com/s?__biz=MzI0MDQ4MTM5NQ==&mid=2247488579&idx=1&sn=f0248519c5d33fd1598af8427e90dfc3&chksm=e91b715fde6cf849395e78cee4d8a2d74a2944fd3934cae8f929182b43b591c51ca8fd9cfb6c&mpshare=1&scene=23&srcid=0220JVhnq2eStE5trGO5HVfX#rd)
-数据库：同义词、sqlserver关闭约束




### 优秀网站
- [【enet硅谷动力】](http://www.enet.com.cn/)
- [【微软虚拟学院官网视频教程】](https://mva.microsoft.com/)


### 待征服
- [【autofac】](https://autofaccn.readthedocs.io/zh/latest/index.html)
- [【Orchard的vNext版】](https://github.com/OrchardCMS/Brochard)
- [【html5页面的样板】](https://github.com/h5bp/html5-boilerplate)
- [【EntityFramework的功能增强】](https://github.com/loresoft/EntityFramework.Extended)
- [【非常短小精悍的后台任务组件】](https://github.com/HangfireIO/Hangfire )
- [【监测.NET后端和Web前端每一个步骤的耗时毫秒数，可查看EF生成的SQL】](https://github.com/MiniProfiler/dotnet )
- [【微信公众平台SDK的C#版，包括企业号的SDK】](https://github.com/JeffreySu/WeiXinMPSDK)

- [【设计模式】](https://www.cnblogs.com/zhili/p/DesignPatternSummery.html)
- [【 C#基础知识】](https://www.cnblogs.com/sunzhenyong/category/510095.html)
- [【window debug】]()
- [【fiddler】]()
- [【领域、事件总线】]()
- [【异步、多线程、响应式、分布式】]()
- [【knockoutjs、jquery】]()
- [【css、css3、html、html5、coffee.js、scss】]()
- [【abp】]()
- [【git、消息队列、redis、ngex、docker、iis、linux、正则、powershell脚本、go、python、java、c、jit/clr】]()
