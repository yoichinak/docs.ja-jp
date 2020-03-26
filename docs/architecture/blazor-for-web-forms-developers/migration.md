---
title: Web フォームからブラゾールへの移行ASP.NET
description: 既存の ASP.NET Web フォーム アプリを Blazor に移行する方法について説明します。
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134090"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Web フォームからブラゾールへの移行ASP.NET

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

コード ベースを ASP.NET Web フォームから Blazor に移行することは、計画を立てる必要がある時間のかかる作業です。 この章では、プロセスの概要を説明します。 移行を容易にする方法は、アプリが*N 層*アーキテクチャに準拠していることを確認することです。 このようにレイヤを論理的に分離することで、.NET Core と Blazor に移行する必要がある内容が明確になります。

この例では[、GitHub](https://github.com/dotnet-architecture/eShopOnBlazor)で利用可能な eShop アプリが使用されます。 eShop は、フォームの入力と検証を介して CRUD 機能を提供するカタログ サービスです。

作業アプリを Blazor に移行する必要がある理由 何度も、必要はありません。 ASP.NET Web フォームは長年にわたってサポートされます。 ただし、Blazor が提供する機能の多くは、移行されたアプリでのみサポートされています。 このような機能は次のとおりです。

- フレームワークのパフォーマンスの向上など`Span<T>`
- Web アセンブリとして実行する機能
- Linux と macOS のクロスプラットフォームサポート
- 他のアプリに影響を与えることなく、アプリローカル展開または共有フレームワーク展開

これらの新機能やその他の新機能が十分に魅力的な場合は、アプリの移行に価値がある可能性があります。 移行は異なる形状をとることができます。これは、アプリ全体、または変更を必要とする特定のエンドポイントのみです。 移行の決定は、最終的には、開発者が解決するビジネス上の問題に基づいています。

## <a name="server-side-versus-client-side-hosting"></a>サーバー側とクライアント側のホスティング

[ホスティング モデル](hosting-models.md)の章で説明したように、Blazor アプリは、サーバー側とクライアント側の 2 つの異なる方法でホストできます。 サーバー側モデルでは、コア SignalR 接続ASP.NET使用して、サーバー上で実際のコードを実行しながら DOM の更新を管理します。 クライアント側モデルはブラウザ内で WebAssembly として動作し、サーバー接続は必要ありません。 特定のアプリに最適な影響を及ぼす可能性のある相違点がいくつかあります。

- WebAssembly として実行はまだ開発中であり、現在の時点ですべての機能 (スレッドなど) をサポートしていない可能性があります。
- クライアントとサーバー間の通信が通信を行うと、サーバー側モードで遅延の問題が発生する場合がある
- データベースおよび内部サービスまたは保護されたサービスへのアクセスには、クライアント側のホスティングを伴う個別のサービスが必要です。

執筆時点では、サーバー側モデルは Web フォームに似ています。 この章の大部分は、運用準備が整っているサーバー側のホスティング モデルに焦点を当てています。

## <a name="create-a-new-project"></a>新しいプロジェクトを作成する

この移行の最初の手順では、新しいプロジェクトを作成します。 このプロジェクトの種類は、.NET Core の SDK スタイル プロジェクトに基づいており、以前のプロジェクト形式で使用されていた定型の大部分を簡略化します。 詳細については、「[プロジェクト構造](project-structure.md)」の章を参照してください。

プロジェクトを作成したら、前のプロジェクトで使用されていたライブラリをインストールします。 以前のバージョンの Web フォーム プロジェクトでは *、packages.config*ファイルを使用して必要な NuGet パッケージを一覧表示している場合があります。 新しい SDK スタイルのプロジェクトでは *、packages.config*が`<PackageReference>`プロジェクト ファイル内の要素に置き換えられました。 この方法の利点は、すべての依存関係が推移的にインストールされるということです。 関心がある最上位の依存関係のみを一覧表示します。

使用している依存関係の多くは、Entity Framework 6 と log4net を含む .NET Core で使用できます。 .NET Core または .NET 標準バージョンが利用できない場合は、.NET Framework バージョンを使用できます。 実際のメリットはケースによって異なります。 NET Core で使用できない API を使用すると、ランタイム エラーが発生します。 このようなパッケージが通知されます。 **ソリューション エクスプローラ**のプロジェクトの **[参照]** ノードに黄色のアイコンが表示されます。

Blazor ベースの eShop プロジェクトでは、インストールされているパッケージを確認できます。 以前は *、packages.config*ファイルには、プロジェクトで使用されるすべてのパッケージが一覧表示され、ファイルの長さは 50 行近くになります。 *パッケージ.config*のスニペットは次のとおりです。

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

要素`<packages>`には、必要なすべての依存関係が含まれます。 これらのパッケージの中に含まれているパッケージは、パッケージが必要なため、識別するのが難しくなります。 必要`<package>`な依存関係のニーズを満たすために、一部の要素が単純に一覧表示されます。

Blazor プロジェクトには、プロジェクト ファイル内の要素`<ItemGroup>`内で必要な依存関係が一覧表示されます。

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Web フォーム開発者の生活を簡素化する NuGet パッケージの 1 つに[、 Windows 互換機能パック](../../core/porting/windows-compat-pack.md)があります。 .NET Core はクロスプラットフォームですが、一部の機能は Windows でのみ使用できます。 Windows 固有の機能は、互換機能パックをインストールすることによって利用可能になります。 このような機能の例としては、レジストリ、WMI、ディレクトリ サービスなどがあります。 このパッケージは約 20,000 の API を追加し、すでに使い慣れた多くのサービスをアクティブ化します。 eShop プロジェクトには互換パックは必要ありません。ただし、プロジェクトで Windows 固有の機能を使用している場合、パッケージは移行作業を容易にします。

## <a name="enable-startup-process"></a>スタートアップ プロセスを有効にする

Blazor の起動プロセスは Web フォームから変更され、他の ASP.NET コア サービスでも同様の設定に従っています。 ホストされたサーバー側の場合、Blazor コンポーネントは通常の ASP.NET Core アプリの一部として実行されます。 WebAssembly を使用してブラウザでホストする場合、Blazor コンポーネントは同様のホスティング モデルを使用します。 違いは、コンポーネントがバックエンドプロセスとは別のサービスとして実行される点です。 いずれにせよ、スタートアップは似ています。

*Global.asax.cs*ファイルは、Web フォーム プロジェクトの既定のスタートアップ ページです。 eShop プロジェクトでは、このファイルは制御の反転 (IoC) コンテナーを構成し、アプリまたは要求のさまざまなライフ サイクル イベントを処理します。 これらのイベントの一部はミドルウェア (など`Application_BeginRequest`) で処理されます。 その他のイベントでは、依存関係注入 (DI) を介して特定のサービスをオーバーライドする必要があります。

例として、eShop の*Global.asax.cs*ファイルには、次のコードが含まれています。

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// http://docs.autofac.org/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

上記のファイルは、`Startup`サーバー側の Blazor のクラスになります。

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

Web フォームから見た重要な変更点の 1 つは、DI の顕著さです。 DIは、ASP.NETコア設計の指針となっています。 コア フレームワークのほぼすべての側面のカスタマイズASP.NETサポートします。 多くのシナリオで使用できる組み込みのサービス プロバイダーもあります。 さらにカスタマイズが必要な場合は、多くのコミュニティ プロジェクトでサポートできます。 たとえば、サードパーティの DI ライブラリへの投資を繰り越すことができます。

元の eShop アプリでは、セッション管理のためのいくつかの構成があります。 サーバー側の Blazor は通信にASP.NETコア SignalR を使用するため、HTTP コンテキストとは無関係に接続が発生する可能性があるため、セッション状態はサポートされません。 セッション状態を使用するアプリでは、Blazor アプリとして実行する前に再設計する必要があります。

アプリの起動の詳細については、「[アプリの起動](app-startup.md)」を参照してください。

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>HTTP モジュールとハンドラをミドルウェアに移行する

HTTP モジュールとハンドラーは、HTTP 要求パイプラインを制御する Web フォームの一般的なパターンです。 受信要求を`IHttpModule`実装`IHttpHandler`または登録して処理できるクラス。 Web フォームは *、web.config*ファイル内のモジュールとハンドラーを構成します。 Web フォームは、アプリのライフサイクル イベント処理にも大きく依存しています。 ASP.NETコアはミドルウェアを代わりに使用します。 ミドルウェアはクラスの`Configure`メソッドに登録されます`Startup`。 ミドルウェアの実行順序は、登録順によって決まります。

[[スタートアップ プロセスを有効にする](#enable-startup-process)] セクションで、Web フォームによって`Application_BeginRequest`メソッドとしてライフサイクル イベントが発生しました。 このイベントは、ASP.NET Core では使用できません。 この動作を実現する 1 つの方法は *、Startup.cs*ファイルの例に示すようにミドルウェアを実装することです。 このミドルウェアは同じロジックを実行し、その後、ミドルウェア パイプラインの次のハンドラーに制御を転送します。

モジュールとハンドラーの移行の詳細については、「 [HTTP ハンドラーとモジュールを core ミドルウェアに移行する 」ASP.NET](/aspnet/core/migration/http-modules)参照してください。

## <a name="migrate-static-files"></a>静的ファイルの移行

静的ファイル (HTML、CSS、画像、JavaScript など) を提供するには、ミドルウェアによってファイルを公開する必要があります。 メソッドを`UseStaticFiles`呼び出すと、Web ルート パスから静的ファイルを提供できるようになります。 デフォルトの web ルート ディレクトリは*wwwroot*ですが、カスタマイズできます。 eShopの`Configure``Startup`クラスのメソッドに含まれているように:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

eShop プロジェクトでは、基本的な静的ファイルアクセスが可能です。 静的ファイル アクセスには、多くのカスタマイズを使用できます。 デフォルトファイルまたはファイルブラウザを有効にする方法については[、「ASP.NETコアの静的ファイル](/aspnet/core/fundamentals/static-files)」を参照してください。

## <a name="migrate-runtime-bundling-and-minification-setup"></a>ランタイムのバンドルと縮小の設定を移行する

バンドルと縮小は、特定のファイルの種類を取得するサーバー要求の数とサイズを減らすためのパフォーマンスの最適化手法です。 JavaScript と CSS は、クライアントに送信される前に、何らかの形のバンドルまたは縮小を受けることがよくあります。 ASP.NET Web フォームでは、これらの最適化は実行時に処理されます。 最適化規則は *、App_Start/バンドルConfig.cs*ファイルとして定義されています。 ASP.NET Core では、より宣言的なアプローチが採用されています。 ファイルには、特定の縮小設定と共に、縮小するファイルが一覧表示されます。

バンドルと縮小の詳細については[、「ASP.NET Core で静的アセットをバンドルおよび縮小](/aspnet/core/client-side/bundling-and-minification)する」を参照してください。

## <a name="migrate-aspx-pages"></a>ASPX ページの移行

Web フォーム アプリのページは、*拡張子 .aspx*を持つファイルです。 Web フォーム ページは、多くの場合、Blazor のコンポーネントにマップできます。 Blazor コンポーネントは、*拡張子 .razor*を持つファイルで作成されます。 eShop プロジェクトでは、5 ページが Razor ページに変換されます。

たとえば、詳細ビューは、Web フォーム プロジェクト内の*Details.aspx* *、Details.aspx.cs、* および*Details.aspx.designer.cs*の 3 つのファイルで構成されます。 Blazor に変換する場合、分離コードとマークアップは*Details.razor*に結合されます。 Razor コンパイル *(.designer.cs*ファイルに含まれるものと同等) は*obj*ディレクトリに格納され、既定ではソリューション**エクスプローラー**で表示できません。 Web フォーム ページは、次のマークアップで構成されます。

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

上記のマークアップの分離コードには、次のコードが含まれます。

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

Blazor に変換すると、Web フォーム ページは次のコードに変換されます。

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

コードとマークアップが同じファイルに含まれているのに注意してください。 必要なサービスはすべて、`@inject`属性を使用してアクセス可能になります。 ディレクティブに`@page`従って、このページは`Catalog/Details/{id}`ルートでアクセスできます。 ルートのプレースホルダの`{id}`値は、整数に制限されています。 Web フォームとは異なり、[ルーティング](pages-routing-layouts.md)セクションで説明されているように、Razor コンポーネントは、そのルートと含まれているパラメーターを明示的に示します。 多くの Web フォーム コントロールは、Blazor に対応するものを持たない場合があります。 同じ目的を果たす同等の HTML スニペットが存在することがよくあります。 たとえば、コントロールを`<asp:Label />`HTML`<label>`要素に置き換えることができます。

### <a name="model-validation-in-blazor"></a>ブラゾールでのモデル検証

Web フォーム コードに検証が含まれている場合は、ほとんど変更を加えなくても、多くの情報を転送できます。 Blazor で実行する利点は、カスタム JavaScript を必要とせずに同じ検証ロジックを実行できることです。 データ注釈を使用すると、モデルの検証が容易になります。

たとえば *、Create.aspx*ページには検証を含むデータ入力フォームがあります。 スニペットの例は次のようになります。

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

Blazor では、同等のマークアップが*Create.razor*ファイルで提供されます。

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

コンテキスト`EditForm`には検証サポートが含まれており、入力をラップできます。 データ注釈は、検証を追加する一般的な方法です。 このような検証サポートは、コンポーネントを`DataAnnotationsValidator`介して追加できます。 このメカニズムの詳細については[、「core Blazor のフォームと検証ASP.NET」](/aspnet/core/blazor/forms-validation)を参照してください。

## <a name="migrate-built-in-web-forms-controls"></a>組み込みの Web フォーム コントロールを移行する

*このコンテンツはまもなく公開されます。*

## <a name="migrate-configuration"></a>構成の移行

Web フォーム プロジェクトでは、構成データは *、web.config*ファイルに格納されるのが最も一般的です。 構成データには、 を`ConfigurationManager`使用してアクセスします。 オブジェクトを解析するためには、サービスがしばしば必要でした。 NET Framework 4.7.2 では、構成可能性が を使用`ConfigurationBuilders`して構成に追加されました。 これらのビルダーを使用すると、開発者は、必要な値を取得するために実行時に構成された構成のさまざまなソースを追加することができました。

ASP.NET Core では、アプリとデプロイで使用される構成ソースを定義できる柔軟な構成システムが導入されました。 Web`ConfigurationBuilder`フォーム アプリで使用できるインフラストラクチャは、ASP.NET コア構成システムで使用される概念に基づきます。

次のスニペットは、Web フォーム eShop プロジェクトが*web.config*を使用して構成値を格納する方法を示しています。

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

データベース接続文字列などのシークレットは、 *web.config*内に格納されるのが一般的です。シークレットは、ソース管理などのセキュリティで保護されていない場所に保持されます。 ASP.NETコア上の Blazor を使用すると、上記の XML ベースの構成は次の JSON に置き換えられます。

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON はデフォルトの設定形式です。ただし、ASP.NET Core では、XML など、他の多くの形式がサポートされています。 コミュニティでサポートされている形式もいくつかあります。

Blazor プロジェクトのクラスの`Startup`コンストラクターは、コンストラクターインジェ`IConfiguration`クションと呼ばれる DI テクニックを使用してインスタンスを受け入れます。

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

デフォルトでは、環境変数、JSON ファイル (*appsettings.json*および*appsettings.{environment}.json)、* およびコマンドラインオプションは、有効な構成ソースとして設定オブジェクトに登録されます。 構成ソースには、 を介`Configuration[key]`してアクセスできます。 より高度な手法は、オプション パターンを使用して構成データをオブジェクトにバインドすることです。 構成とオプション パターンの詳細については、ASP.NET[コアの ASP.NET コア](/aspnet/core/fundamentals/configuration/)および[オプション パターンの](/aspnet/core/fundamentals/configuration/options)構成をそれぞれ参照してください。

## <a name="migrate-data-access"></a>データ アクセスの移行

データ アクセスは、アプリの重要な側面です。 eShop プロジェクトは、カタログ情報をデータベースに格納し、エンティティ フレームワーク (EF) 6 を使用してデータを取得します。 EF 6 は .NET Core 3.0 でサポートされているため、プロジェクトは引き続き EF 6 を使用できます。

eShop には、次の EF 関連の変更が必要でした。

- .NET Framework では`DbContext`、オブジェクトは*name=ConnectionString*という形式の文字列`ConfigurationManager.AppSettings[ConnectionString]`を受け取り、接続文字列を使用して接続します。 NET Core では、これはサポートされていません。 接続文字列を指定する必要があります。
- データベースは同期的にアクセスされました。 この方法は機能しますが、スケーラビリティが低下する可能性があります。 このロジックは、非同期パターンに移動する必要があります。

データセットのバインドに対して同じネイティブ サポートはありませんが、Blazor は、Razor ページでの C# サポートで柔軟性と機能を提供します。 たとえば、計算を実行して結果を表示できます。 Blazor のデータパターンの詳細については、[データアクセス](data.md)の章を参照してください。

## <a name="architectural-changes"></a>アーキテクチャの変更

最後に、Blazor への移行時に考慮すべき重要なアーキテクチャの違いがいくつかあります。 これらの変更の多くは、.NET Core または ASP.NET コアに基づくすべての機能に適用できます。

Blazor は .NET Core 上で構築されているため、.NET Core でのサポートを確保する際に考慮すべき点があります。 主な変更点には、次の機能の削除が含まれます。

- 複数のアプリケーションドメイン
- リモート処理
- CAS (コード アクセス セキュリティ)
- セキュリティ透過性

NET Core での実行をサポートするために必要な変更を特定する方法の詳細については[、「.NET Framework から .NET Core へのコードの移植](/dotnet/core/porting)」を参照してください。

ASP.NET Core は、ASP.NETの再考されたバージョンであり、最初は明らかに見えない変更があります。 主な変更点は次のとおりです。

- 同期コンテキストがないため、、、、または`HttpContext.Current``Thread.CurrentPrincipal`他の静的アクセサーが存在しません。
- シャドウ コピーなし
- 要求キューがありません

ASP.NET Core の操作の多くは非同期であり、I/O バインド タスクの読み込みが容易になります。 を`Task.Wait()``Task.GetResult()`使用してブロックすることは重要です。

## <a name="migration-conclusion"></a>移行の結論

この時点で、Web フォーム プロジェクトを Blazor に移動するために必要な例が数多く見られました。 完全な例については[、eShopOnBlazor](https://github.com/dotnet-architecture/eShopOnBlazor)プロジェクトを参照してください。

>[!div class="step-by-step"]
>[前へ](security-authentication-authorization.md)
