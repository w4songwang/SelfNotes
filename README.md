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
