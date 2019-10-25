---
ms.openlocfilehash: be9a79f6ead3e72d7ffaade758704f0c1e2477f0
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394305"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a>ホスティング: 汎用ホストによる Startup コンストラクター挿入の制限

汎用ホストが `Startup` クラスのコンストラクター挿入でサポートする型は、`IHostEnvironment`、`IWebHostEnvironment`、`IConfiguration` だけです。 `WebHost` を使用しているアプリは影響を受けません。

#### <a name="change-description"></a>変更の説明

ASP.NET Core 3.0 より前では、コンストラクター挿入は `Startup` クラスのコンストラクターの任意の型に使用できました。 ASP.NET Core 3.0 では、Web スタックが汎用ホスト ライブラリに再プラットフォーム化されました。 この変更は、テンプレートの *Program.cs* ファイルで確認できます。

**ASP.NET Core 2.x:**

<https://github.com/aspnet/AspNetCore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

**ASP.NET Core 3.0:**

<https://github.com/aspnet/AspNetCore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

`Host` では、1 つの依存関係挿入 (DI) コンテナーを使用してアプリをビルドします。 `WebHost` ホストでは 2 つのコンテナーを使用します。1 つがホスト用、もう 1 つがアプリ用です。 これにより、`Startup` コンストラクターでは、カスタム サービス挿入がサポートされなくなりました。 挿入できるのは、`IHostEnvironment`、`IWebHostEnvironment`、`IConfiguration` だけです。 この変更により、シングルトン サービスの重複作成などの DI の問題を防ぐことができます。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="reason-for-change"></a>変更理由

この変更は、汎用ホスト ライブラリへの Web スタックの再プラットフォーム化の結果です。

#### <a name="recommended-action"></a>推奨される操作

サービスを `Startup.Configure` メソッド シグネチャに挿入します。 次に例を示します。

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
