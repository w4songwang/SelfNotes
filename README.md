### 马克飞象 MarkDown在线编辑
<https://maxiang.io/>
<http://www.williamlong.info/archives/4319.html>




### 字符串MD5加密成guid
``` python
public static Guid EncryptWithMD5(string source)
{
    byte[] sor = Encoding.UTF8.GetBytes(source);
    MD5 md5 = MD5.Create();
    byte[] result = md5.ComputeHash(sor);
    return new Guid(result);
}
``` 
