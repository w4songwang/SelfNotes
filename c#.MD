### [C# EPPlus对Excel 单元格格式, 及行高、 列宽、 单元格边框线、 冻结设置](https://blog.csdn.net/weixin_33805743/article/details/90103488)



### epplus设置单个单元格字体样式
``` c#
using (ExcelPackage package = new ExcelPackage(fi))
{
    // add a new worksheet to the empty workbook
    ExcelWorksheet worksheet = package.Workbook.Worksheets["Inv"];

    //add multi-coloured text to a cell
    worksheet.Cells[2, 1].IsRichText = true;
    ExcelRichTextCollection rtfCollection = worksheet.Cells[2, 1].RichText;
    ExcelRichText ert = rtfCollection.Add("bugaga");
    ert.Bold = true;
    ert.Color = System.Drawing.Color.Red;
    ert.Italic = true;

    ert = rtfCollection.Add("alohaaaaa");
    ert.Bold = true;
    ert.Color = System.Drawing.Color.Purple;
    ert.Italic = true;

    ert = rtfCollection.Add("mm");
    ert.Color = System.Drawing.Color.Peru;
    ert.Italic = false;
    ert.Bold = false;

    package.Save();
}
``` 

### [C# Office操作](http://www.e-iceblue.cn/)


### [C# WebApi缓存](https://github.com/filipw/Strathweb.CacheOutput)


### 对List进行分组排序后输出
``` c#
public class Student
{
    public int ID { get; set; }
    public string Name { get; set; }
    public int Age { get; set; }
    public string Sex { get; set; }
}


List<Student> lsStudent = new List<Student>()
{
    new Student { ID = 1 ,Name = "1", Age = 25, Sex = "男" },
    new Student { ID = 2, Name = "2", Age = 18, Sex = "女" },
    new Student { ID = 3, Name = "3", Age = 13, Sex = "男" },
    new Student { ID = 4, Name = "4", Age = 23, Sex = "男" },
    new Student { ID = 5, Name = "5", Age = 22, Sex = "女" }
};
 //先输出所有的男，在输出所有的女
foreach (IGrouping<string, Student> group in lsStudent.GroupBy(x => x.Sex))
{
    Console.WriteLine("当前学生的性别是:{0}", group.Key);
    foreach (Student student in group.OrderBy(a => a.Age))//不排序直接输出的话：Student student in group
    {
        Console.WriteLine("姓名：" + student.Name + " 年龄：" + student.Age);
    }
}

``` 



### HttpClient
``` c#
 using (var client = new HttpClient(new HttpClientHandler { UseCookies = true }))
 {
     client.DefaultRequestHeaders.Add("AcceptDomain", "AllDomain");
     //登录设置cookie
     var path = "http://localhost/aspe023/api/v1/device/channellist?serial=" ;
     var response = client.GetAsync(path).Result;
     var result = response.Content.ReadAsStringAsync().Result;
     var channelResponseDto = JsonConvert.DeserializeObject<int>(result);
 }

``` 

### [C# Winform UI  MetroModernUI](https://blog.csdn.net/lgj123xj/article/details/79592183)


### [代码生成器 Scaffolder T4]()




### ef在sql server生成数据库时生成字段说明
``` c#

    public static class TableFieldDescriptionInit
    {
        public static void Init(Database context)
        {
            Task.Run(() =>
            {
                var currentAssembly = Assembly.GetExecutingAssembly();
                var types = currentAssembly
                    .GetTypes()
                    .Where(x => x.IsClass && x.GetCustomAttributes(typeof(TableAttribute)).Any())//Type是类并且包含自定义TableAttribute属性
                    .ToList();
                var tables = types.Select(x => new TablePropertyInfo()
                {
                    TableName = x.GetAttributeValue((TableAttribute ta) => ta.Name),
                    Peroperties = x.GetProperties(BindingFlags.Public | BindingFlags.Instance).ToList()
                }).ToList();
                SetDescription(tables, context);
            });

        }

        /// <summary>
        /// 设置数据库表字段说明
        /// </summary>
        /// <param name="tables"></param>
        /// <param name="context"></param>
        private static void SetDescription(List<TablePropertyInfo> tables, Database context)
        {
            tables.ForEach(table =>
            {
                if (string.IsNullOrWhiteSpace(table.TableName) || table.Peroperties == null || !tables.Any()) return;
                table.Peroperties.ForEach(peropery =>
                {
                    var objs = peropery.GetCustomAttributes(typeof(DescriptionAttribute), true);
                    if (!objs.Any()) return;
                    var description = ((DescriptionAttribute)objs[0]).Description;
                    if (string.IsNullOrWhiteSpace(description)) return;
                    var sql = $"EXECUTE sp_addextendedproperty N'MS_Description', N'{description}', N'user', N'dbo', N'table', N'{table.TableName}', N'column', N'{peropery.Name}'";
                    context.ExecuteSqlCommand(sql);
                });
            });
        }
    }

    /// <summary>
    /// 获取属性值
    /// </summary>
    public static class AttributeExtensions
    {
        public static TValue GetAttributeValue<TAttribute, TValue>(
            this Type type,
            Func<TAttribute, TValue> valueSelector)
            where TAttribute : Attribute
        {
            var att = type.GetCustomAttributes(
                typeof(TAttribute), true
            ).FirstOrDefault() as TAttribute;
            return att != null ? valueSelector(att) : default(TValue);
        }
    }
    public class TablePropertyInfo
    {
        public string TableName { get; set; }
        public List<PropertyInfo> Peroperties { get; set; }
    }
``` 
