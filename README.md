
# 簡介

運作架構

![](http://i.imgur.com/zjKJX3e.png)

Controller 的 Method 預設都是可被呼叫, 除非明確標記非 Web Action

```
[NonAction] 
public string SimpleMethod()
{ 
   return "Hi, I am not action method";
}
```

# 目錄結構
```
|   favicon.ico
|   Global.asax / Global.asax.cs ; 全域的 ASP.NET class，用來註冊一些專案啟動所需的設定檔，並且進行一些初始化，或是專案預期外狀態，以及處理 unhandled exception 用
|   packages.config ; 相依套件清單
|   Project_Readme.html
|   Startup.cs
|   Web.config  ; 是整個專案的設定檔
|   Web.Debug.config
|   Web.Release.config
|   WebApplication1.csproj
|   WebApplication1.csproj.user
|   
+---App_Data    ; 放置 private data 的地方，像是 XML files, DB files 等等
+---App_Start   ; 放置設定檔 (Config) 的地方，像是 WebApi, Route, Auth, Filter 
|       BundleConfig.cs
|       FilterConfig.cs
|       IdentityConfig.cs
|       RouteConfig.cs
|       Startup.Auth.cs
|       
+---bin ; 編譯過後的檔案，例如 dll 檔
|   |   Antlr3.Runtime.dll
|   |   Antlr3.Runtime.pdb
|   |   EntityFramework.dll
|   |   EntityFramework.SqlServer.dll
|   |   EntityFramework.SqlServer.xml
|   |   EntityFramework.xml
|   |   Microsoft.AspNet.Identity.Core.dll
|   |   Microsoft.AspNet.Identity.Core.xml
|   |   Microsoft.AspNet.Identity.EntityFramework.dll
|   |   Microsoft.AspNet.Identity.EntityFramework.xml
|   |   Microsoft.AspNet.Identity.Owin.dll
|   |   Microsoft.AspNet.Identity.Owin.xml
|   |   Microsoft.CodeDom.Providers.DotNetCompilerPlatform.dll
|   |   Microsoft.CodeDom.Providers.DotNetCompilerPlatform.xml
|   |   Microsoft.Owin.dll
|   |   Microsoft.Owin.Host.SystemWeb.dll
|   |   Microsoft.Owin.Host.SystemWeb.xml
|   |   Microsoft.Owin.Security.Cookies.dll
|   |   Microsoft.Owin.Security.Cookies.xml
|   |   Microsoft.Owin.Security.dll
|   |   Microsoft.Owin.Security.Facebook.dll
|   |   Microsoft.Owin.Security.Facebook.xml
|   |   Microsoft.Owin.Security.Google.dll
|   |   Microsoft.Owin.Security.Google.xml
|   |   Microsoft.Owin.Security.MicrosoftAccount.dll
|   |   Microsoft.Owin.Security.MicrosoftAccount.xml
|   |   Microsoft.Owin.Security.OAuth.dll
|   |   Microsoft.Owin.Security.OAuth.xml
|   |   Microsoft.Owin.Security.Twitter.dll
|   |   Microsoft.Owin.Security.Twitter.xml
|   |   Microsoft.Owin.Security.xml
|   |   Microsoft.Owin.xml
|   |   Microsoft.Web.Infrastructure.dll
|   |   Newtonsoft.Json.dll
|   |   Newtonsoft.Json.xml
|   |   Owin.dll
|   |   System.Web.Helpers.dll
|   |   System.Web.Helpers.xml
|   |   System.Web.Mvc.dll  ; ASP.NET MVC最主要的程序集
|   |   System.Web.Mvc.xml
|   |   System.Web.Optimization.dll
|   |   System.Web.Optimization.xml
|   |   System.Web.Razor.dll
|   |   System.Web.Razor.xml
|   |   System.Web.WebPages.Deployment.dll
|   |   System.Web.WebPages.Deployment.xml
|   |   System.Web.WebPages.dll
|   |   System.Web.WebPages.Razor.dll
|   |   System.Web.WebPages.Razor.xml
|   |   System.Web.WebPages.xml
|   |   WebApplication1.dll
|   |   WebApplication1.dll.config
|   |   WebApplication1.pdb
|   |   WebGrease.dll
|   |   
|   \---roslyn
|           csc.exe
|           Microsoft.Build.Tasks.CodeAnalysis.dll
|           Microsoft.CodeAnalysis.CSharp.dll
|           Microsoft.CodeAnalysis.dll
|           Microsoft.CodeAnalysis.VisualBasic.dll
|           Microsoft.CSharp.Core.targets
|           Microsoft.VisualBasic.Core.targets
|           System.Collections.Immutable.dll
|           System.Reflection.Metadata.dll
|           vbc.exe
|           VBCSCompiler.exe
|           VBCSCompiler.exe.config
|           
+---Content ; 放置一些靜態的檔案，像是 CSS 與 Image 檔案
|       bootstrap.css
|       bootstrap.min.css
|       Site.css
|       
+---Controllers ; 放 MVC 當中 Controller 的位置
|       AccountController.cs
|       HomeController.cs
|       ManageController.cs
|       
+---fonts
|       glyphicons-halflings-regular.eot
|       glyphicons-halflings-regular.svg
|       glyphicons-halflings-regular.ttf
|       glyphicons-halflings-regular.woff
|       
+---Models ; 放 MVC 當中的 Models 的位置，像是一些 Database 的欄位定義檔
|       AccountViewModels.cs
|       IdentityModels.cs
|       ManageViewModels.cs
|       
+---Properties
|       AssemblyInfo.cs
|       
+---Scripts ; 放置 Javascript 的地方，包括 Javascript library (ex. jQuery)
|       bootstrap.js
|       bootstrap.min.js
|       jquery-1.10.2.intellisense.js
|       jquery-1.10.2.js
|       jquery-1.10.2.min.js
|       jquery-1.10.2.min.map
|       jquery.validate-vsdoc.js
|       jquery.validate.js
|       jquery.validate.min.js
|       jquery.validate.unobtrusive.js
|       jquery.validate.unobtrusive.min.js
|       modernizr-2.6.2.js
|       respond.js
|       respond.min.js
|       _references.js
|       
\---Views ; 放 View 跟 partial views 的地方，通常會分資料夾，並跟 Controller 定義同個名字，例如有個 Controller 叫做 HomeController.cs，則 Views 下面就會有一個 Home 資料夾
    |   Web.config ; 放置這個 config 的目的在於避免 IIS 讀取到 View 的路徑，因為理論上 View 只能透過 Controller 來讀取才對
    |   _ViewStart.cshtml ; 指全部畫面都會用到的 HTML 內容
    |   
    +---Account
    |       ConfirmEmail.cshtml
    |       ExternalLoginConfirmation.cshtml
    |       ExternalLoginFailure.cshtml
    |       ForgotPassword.cshtml
    |       ForgotPasswordConfirmation.cshtml
    |       Login.cshtml
    |       Register.cshtml
    |       ResetPassword.cshtml
    |       ResetPasswordConfirmation.cshtml
    |       SendCode.cshtml
    |       VerifyCode.cshtml
    |       _ExternalLoginsListPartial.cshtml
    |       
    +---Home
    |       About.cshtml
    |       Contact.cshtml
    |       Index.cshtml
    |       
    +---Manage
    |       AddPhoneNumber.cshtml
    |       ChangePassword.cshtml
    |       Index.cshtml
    |       ManageLogins.cshtml
    |       SetPassword.cshtml
    |       VerifyPhoneNumber.cshtml
    |       
    \---Shared  ; 指的是不同 Controller 共用的 Views 檔案
            Error.cshtml
            Lockout.cshtml
            _Layout.cshtml
            _LoginPartial.cshtml
            
```

# MVC 檔案對應

以路徑 /Home/Index 為例

## Controller

/Controllers/HomeController.cs

```
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
using System.Web.Mvc;

namespace WebApplication1.Controllers
{
    public class HomeController : Controller
    {
        public ActionResult Index() // 對應到 /Views/Home/Index.html
        {
            return View();
        }

        public ActionResult About()
        {
            ViewBag.Message = "Your application description page.";

            return View();
        }

        public ActionResult Contact()
        {
            ViewBag.Message = "Your contact page.";

            return View();
        }
    }
}
```

### 使用共用 View

```
// 使用共享的 View
public ActionResult Error()
{
    return View("Error"); // Views/Shared/Error.cshtml
}
```


## View

```
/Views/Home/
    - Index.html
```

* View 使用 ViewData["key"] = Value  的資料, 於 View 中使用 @變數 來取得資料
* 如果要使用 C# 語法, 則放在 @{} 區塊中

```
@{
    Response.Write(ViewData["Name"]);
}
```

* ViewData和ViewBag 是Contoller與View之間值傳遞的內容

### 使用 Model 更新 View

```
// Controller
public ActionResult ViewWithModel()
{
    var arick = new ArickViewModel();
    arick.Name = "Arick";
    return View("ViewWithModel", arick);
}

// View

@model WebApplication1.Models.ArickViewModel

@{
    ViewBag.Title = "ViewWithModel";
}

<h2>ViewWithModel</h2>

<div>@Model.Name
    </div>
```

### 使用陣列的 Model 更新 View

```
// Model
public class AricksViewModel
{
    public List<ArickViewModel> Data = new List<ArickViewModel>();
}

// Controller
public ActionResult ViewWithModel2()
{

    var aricks = new AricksViewModel();
    var arick1 = new ArickViewModel();
    arick1.Name = "Arick";
    aricks.Data.Add(arick1);

    var arick2 = new ArickViewModel();
    arick2.Name = "Chui-Wen Chiu";
    aricks.Data.Add(arick2);

    return View("ViewWithModel2", aricks);
}

// View
@using WebApplication1.Models
@model AricksViewModel
@{
    ViewBag.Title = "ViewWithModel2";
}

<h2>ViewWithModel2</h2>
@foreach(ArickViewModel v in Model.Data)
{
<div>@v.Name</div>
}


```

# 取得 Form Post 資料

```
// 方法一：通過Request.Form
[HttpPost]
public ActionResult Test()
{
    string id=Request.Form["id"];
    return View();
}
        
// 方法二：通過映射到FormCollection
[HttpPost]
public ActionResult Test(FormCollection form)
{
    string id = form["id"];
    return View();
}
        
// 方法三：通過映射到控制器方法參數
[HttpPost]
public ActionResult Test(string id)
{
    //id是獲取來自View表單POST過來的控件名為id的值
    return View();
}
        
//方法四：通過映射到視圖數據對象
[HttpPost]
public ActionResult Test(TModel model)
{
    string id = model.id;
    return View();
}
        
// 方法五：通過調用UpdateModel方法
[HttpPost]
public ActionResult Test()
{
    TModel model;
    UpdateModel<TModel>(model);
    return View();
}
```

* http://www.zuowenjun.cn/post/2014/10/22/63.html

# 回傳 Json

```
public JsonResult DataJsonSave()
{
    return Json(new {success = true });
}
```


* http://nolife.smartdog.tw/Default/Detail/3

# 常用操作

## 新增 Controller

Controllers 目錄右鍵選單 Add | Controller

![](http://www.dotnetfunda.com/UserFiles/ArticlesFiles/Questpond_4672_3.JPG)

## 新增 View

方法1: Views 目錄右鍵選單 Add | View

方法2: 在 Controller Code 的 Method 滑鼠右鍵 Add | View

![](http://www.dotnetfunda.com/UserFiles/ArticlesFiles/Questpond_1996_4.JPG)

## 新增 Model

Models 目錄新增 Class


# 支援 JsonP

```
public class JsonpResult : JsonResult
    {
        public static readonly string JsonpCallbackName = "callback";
        public static readonly string CallbackApplicationType = "application/json";

        public override void ExecuteResult(ControllerContext context)
        {
            if (context == null)
            {
                throw new ArgumentNullException("context");
            }
            if ((JsonRequestBehavior == JsonRequestBehavior.DenyGet) &&
                  String.Equals(context.HttpContext.Request.HttpMethod, "GET", StringComparison.OrdinalIgnoreCase))
            {
                throw new InvalidOperationException();
            }
            var response = context.HttpContext.Response;
            if (!String.IsNullOrEmpty(ContentType))
                response.ContentType = ContentType;
            else
                response.ContentType = CallbackApplicationType;
            if (ContentEncoding != null)
                response.ContentEncoding = this.ContentEncoding;
            if (Data != null)
            {
                String buffer;
                var request = context.HttpContext.Request;
                var serializer = new JavaScriptSerializer();
                if (request[JsonpCallbackName] != null)
                    buffer = String.Format("{0}({1})", request[JsonpCallbackName], serializer.Serialize(Data));//首先根據callback獲取獲取函數名，然後傳入json字符串作為函數參數
                else
                    buffer = serializer.Serialize(Data);
                response.Write(buffer);
            }
        }
    }
    
// Controller Extension    
public static JsonpResult Jsonp(this Controller controller, object data)
        {
            JsonpResult result = new JsonpResult()
            {
                Data = data,
                JsonRequestBehavior = JsonRequestBehavior.AllowGet
            }; 
            return result;
        }
        
// Test
public ActionResult Index()
        {
            return this.Jsonp(new { name = "server JsonpResult" });
        }
```



* [ASP.NET MVC 定义JsonpResult实现跨域请求 - dandzm](http://www.cnblogs.com/dandzm/p/4758453.html)


# 參考資料
* [七天學會ASP.NET MVC](http://my.oschina.net/powertoolsteam/blog/490652)

----
http://www.cnblogs.com/xiaoyaojian/p/4725496.html
使用Donut Caching和Donut Hole Caching在ASP.NET MVC应用中缓存页面 - 小白哥哥


http://www.cnblogs.com/xiaoxuanzhi/p/4733280.html
asp.net web编程开发将model类序列化 - 孔轩志



http://www.c-sharpcorner.com/UploadFile/618722/custom-error-page-in-Asp-Net-mvc/
Custom Error Page in ASP.NET MVC


http://www.c-sharpcorner.com/UploadFile/13048b/model-validation-in-Asp-Net-mvc909/
Model Validation in ASP.NET MVC


http://www.cnblogs.com/oneapm/p/4752261.html
7 天玩转 ASP.NET MVC — 第 6 天 - OneAPM官方技术博客


http://my.oschina.net/oneapmofficial/blog/495954
7 天玩转 Asp.Net Mvc — 第 6 天


http://www.cnblogs.com/luge/p/ASP-NET-LIFE.html
Asp.Net 一个请求的处理流程 - 卤鸽


http://my.oschina.net/u/200350/blog/494664
Asp.Net Mvc 基于角色的权限控制系统的示例教程


http://www.dotblogs.com.tw/rainmaker/archive/2015/08/19/153169.aspx
[ASP.NET]使用 Hangfire 來處理非同步的工作


http://ithelp.ithome.com.tw/question/10175295?tag=rss.qu
asp.net下拉式連動顯示gridview


http://www.c-sharpcorner.com/UploadFile/15208c/how-to-insert-edit-update-and-delete-records-in-gridview-wit/
Perform CRUD Operations in GridView Without Using Database in ASP.NET


http://www.c-sharpcorner.com/UploadFile/ba4d3a/update-and-delete-database-table-using-gridview-in-Asp-Net/
Update and Delete Database Table Using GridView in ASP.NET


http://www.cnblogs.com/jiekzou/p/4772273.html
Asp.Net Mvc4入门到精通系列目录汇总 - 邹琼俊



http://www.cnblogs.com/zhili/p/AspnetIdentity.html
ASP.NET 开发必备知识点(2)：那些年追过的ASP.NET权限管理 - Learning hard


http://www.dotblogs.com.tw/ian/archive/2015/08/31/aspnet-webform-autofac.aspx
[ASP.NET] Autofac IoC Container


http://www.cnblogs.com/xiaoyaojian/p/4768079.html
Asp.Net 5 之 错误诊断和它的中间件们 - 小白哥哥


http://www.cnblogs.com/jiekzou/p/4766701.html
ASP.NET MVC导出excel（数据量大，非常耗时的，异步导出） - 邹琼俊


http://www.c-sharpcorner.com/UploadFile/mscratnesh/data-annotation-in-Asp-Net-mvc/
Data Annotation in ASP.NET MVC


http://my.oschina.net/oneapmofficial/blog/498325
7 天玩转 Asp.Net Mvc — 第 7 天
-=-=-=-=-=-=-=-=-=-=
http://www.cnblogs.com/oneapm/p/4764390.html
7 天玩转 ASP.NET MVC — 第 7 天 - OneAPM官方技术博客


http://www.cnblogs.com/xiaoyaojian/p/4763016.html
在Asp.Net 5应用程序中的跨域请求功能详解 - 小白哥哥


http://www.cnblogs.com/lightluomeng/p/4760220.html
ASP.NET MVC 如何在一个同步方法（非async）方法中等待async方法 - LibraJM


http://www.codeproject.com/Articles/1021765/ASP-NET-MVC-with-JSPM-and-Material-Design-Lite
ASP.NET MVC 6 with JSPM and Material Design Lite


http://www.c-sharpcorner.com/UploadFile/0c1bb2/insert-data-into-database-using-Asp-Net-mvc/
Creating an ASP.NET MVC Application


http://www.cnblogs.com/jiekzou/p/4781205.html
ASP.Net MVC View(视图) - 邹琼俊


http://www.c-sharpcorner.com/UploadFile/89bfaf/how-routing-works-in-Asp-Net-web-api/
How Routing Works In ASP.NET WEB API


http://www.cnblogs.com/jiekzou/p/4780412.html
ASP.Net MVC Controller(控制器) - 邹琼俊


http://www.cnblogs.com/Coloor/p/Coloor.html
ASP.NET MVC下的验证码 - Coloor


http://www.c-sharpcorner.com/UploadFile/c3a146/bind-stack-column-chart-in-Asp-Net-using-jquery-and-ajax/
Bind Stack Column Chart in ASP.NET Using jQuery And Ajax


http://www.cnblogs.com/xiaoyaojian/p/4779553.html
Asp.Net5 中静态文件的各种使用方式 - 小白哥哥


http://www.cnblogs.com/gangtianci/p/4776841.html
ASP.NET WebAPI 03 返回结果 - Barlow Du


http://www.dotblogs.com.tw/yc421206/archive/2015/08/31/153260.aspx
[ASP.NET][Telerik] Export and Import RadGrid Setting


http://www.cnblogs.com/zuowj/p/4772709.html
Asp.Net Mvc必知必会知识点总结（二） - 梦在旅途


http://www.dotblogs.com.tw/grence/archive/2015/08/31/153266.aspx
ASP.NET MVC Authorize
