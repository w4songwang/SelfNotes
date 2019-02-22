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

### 数据库数据同步
``` sql，更新操作=删除旧数据+插入最新数据
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

### docs.microsoft.com 文档
- [NuGet 文档](https://docs.microsoft.com/zh-cn/nuget/)


### 优秀博客
- [鱼东东 - 博客园](https://www.cnblogs.com/yudongdong/)
- [dotNET跨平台](https://me.csdn.net/sD7O95O)
- [零度编程](https://www.xcode.me/)

### 陌生的概念
- [burpsuite、时序分析、QQ关系库](https://mp.weixin.qq.com/s?__biz=MzI0MDQ4MTM5NQ==&mid=2247488579&idx=1&sn=f0248519c5d33fd1598af8427e90dfc3&chksm=e91b715fde6cf849395e78cee4d8a2d74a2944fd3934cae8f929182b43b591c51ca8fd9cfb6c&mpshare=1&scene=23&srcid=0220JVhnq2eStE5trGO5HVfX#rd)
