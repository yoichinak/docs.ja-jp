---
title: <supportedRuntime> 構成要素 - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: c6bf4c6b262bc9066277a683d5eda67ada6f4d08
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2019
ms.locfileid: "66456215"
---
# <a name="supportedruntime-element"></a>\<supportedRuntime > 要素

どの共通言語ランタイムのバージョンと、必要に応じて、アプリケーションの .NET Framework バージョンの指定をサポートしています。  

[\<configuration>](../configuration-element.md)  
&nbsp;&nbsp;[\<startup>](../startup/startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp; **\<supportedRuntime>**  

## <a name="syntax"></a>構文

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|**version**|省略可能な属性です。<br /><br /> このアプリケーションがサポートする共通言語ランタイム (CLR: Common Language Runtime) のバージョンを指定する文字列値。 有効な値について、`version`属性を参照してください、 [「ランタイム バージョン」の値](#version)セクション。 **注:** を通じて、.NET Framework 3.5、"*ランタイム バージョン*"値には、フォーム*メジャー*.*マイナー*.*ビルド*します。 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降では、必要となるのはメジャー バージョン番号とマイナー バージョン番号のみです (つまり、"v4.0.30319" ではなく "v4.0")。 短い文字列を使用することをお勧めします。|
|**sku**|省略可能な属性です。<br /><br /> 在庫管理単位 (SKU) を指定する文字列の値。SKU はこのアプリケーションがサポートする .NET Framework リリースを指定します。<br /><br /> .NET Framework 4.0 以降では、`sku` 属性の使用が推奨されます。  この属性が指定される場合は、アプリケーションが対象とする .NET Framework のバージョンを示します。<br /><br /> Sku 属性の有効な値は、次を参照してください。、 ["sku id"値](#sku)セクション。|

## <a name="remarks"></a>Remarks

場合、  **\<supportedRuntime >** 要素が、アプリケーション構成ファイルに存在しない、アプリケーションをビルドするために使用するランタイムのバージョンが使用されます。

**\<SupportedRuntime >** 1.1 以降、ランタイムのバージョンを使用して構築されたすべてのアプリケーションで要素を使用する必要があります。 ランタイムのバージョン 1.0 をサポートするために構築されたアプリケーションを使用する必要があります、 [ \<requiredRuntime >](../startup/requiredruntime-element.md)要素。

> [!NOTE]
> 使用する場合、 [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)構成ファイルを指定する関数を使用する必要があります、`<requiredRuntime>`ランタイムのすべてのバージョンの要素。 `<supportedRuntime>`を使用する場合、要素は無視されます[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)します。  
  
NET Framework 1.1 から 3.5 までのランタイムの複数のバージョンをサポートするアプリケーションでは、ランタイムの複数のバージョンをサポートする場合は、最初の要素で最も優先度の高いバージョンを指定し、最後の要素で最も優先度の低いバージョンを指定する必要があります。 .NET Framework 4.0 またはそれ以降のバージョンをサポートするアプリ、`version`属性は .NET Framework 4 およびそれ以降のバージョンに一般的では、CLR のバージョンを示します、`sku`属性は 1 つの .NET Framework バージョンを示しますが、アプリケーションが対象とします。 

場合、  **\<supportedRuntime >** を持つ要素、`sku`属性が、構成ファイルに存在し、インストールされている .NET Framework のバージョンが低い指定のサポートされているバージョンのアプリケーション実行に失敗し、代わりに、サポートされているバージョンをインストールするよう求めるメッセージが表示されます。 それ以外の場合、アプリケーションがインストール済みのバージョンで実行しようとしましたが、そのバージョンと完全に互換性がない場合に予期しない動作可能性があります。 (.NET Framework のバージョン間の互換性の相違点、次を参照してください[、.NET Framework アプリケーションの互換性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)。)。そのため、エラーの診断を簡単にアプリケーション構成ファイルには、この要素を含めることをお勧めします。 (新しいプロジェクトを既に作成するときに、Visual Studio によって自動的に生成する構成ファイルが含まれますが。)
  
> [!NOTE]
> アプリケーションがなど、レガシ アクティブ化パスを使用するかどうか、 [CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)、それらのパスを以前のバージョンではなく、CLR の version 4 をアクティブ化して、アプリケーションが .NET Framework に組み込まれている場合、または依存していますが、4、.NET Framework の以前のバージョンでビルドされた混合モードのアセンブリにはサポートされているランタイムの一覧で、.NET Framework 4 を指定するための十分な。 さらに、 [ \<startup > 要素](../startup/startup-element.md)、構成ファイルで設定する必要があります、`useLegacyV2RuntimeActivationPolicy`属性を`true`します。 ただし、この属性を設定`true`ビルドされたランタイムではなく、.NET Framework 4 を使用して .NET Framework の以前のバージョンでビルドされたすべてのコンポーネントが実行されることを意味します。

アプリケーションは、そのアプリケーションを実行できる .NET Framework のすべてのバージョンでテストすることをお勧めします。

<a name="version"></a> 
## <a name="runtime-version-values"></a>"ランタイム バージョン" の値
`runtime`属性が特定のアプリケーションに必要な共通言語ランタイム (CLR) バージョンを指定します。 すべてのバージョンの .NET Framework v4.x の指定、 `v4.0` CLR。 次の表に、有効な値、*ランタイム バージョン*の値、`version`属性。

|.NET Framework のバージョン|`version` 属性|
|----------------------------|-------------------------|
|1|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku"></a> "sku id"値

`sku`属性では、ターゲット フレームワーク モニカー (TFM) を使用して、アプリが対象とし、実行に必要とする .NET Framework のバージョンを示します。 次の表に、有効な値でサポートされている、`sku`属性、.NET Framework 4 以降します。

|.NET Framework のバージョン|`sku` 属性|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0, Client Profile|".NETFramework,Version=v4.0,Profile=Client"|
|4.0, platform update 1|".NETFramework,Version=v4.0.1"|
|4.0, Client Profile, update 1|".NETFramework,Version=v4.0.1,Profile=Client"|
|4.0, platform update 2|".NETFramework,Version=v4.0.2"|
|4.0, Client Profile, update 2|".NETFramework,Version=v4.0.2,Profile=Client"|
|4.0, platform update 3|".NETFramework,Version=v4.0.3"|
|4.0, Client Profile, update 3|".NETFramework,Version=v4.0.3,Profile=Client"|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|".NETFramework,Version=v4.6.2"|
|4.7|".NETFramework,Version=v4.7"|
|4.7.1|".NETFramework,Version=v4.7.1"|
|4.7.2|".NETFramework,Version=v4.7.2"|
|4.8|".NETFramework,Version=v4.8"|

## <a name="example"></a>例

サポートされているランタイムのバージョンを構成ファイルで指定する例を次に示します。 構成ファイルでは、アプリが .NET Framework 4.7 を対象とすることを示します。

```xml
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7" />
   </startup>
</configuration>
```

## <a name="configuration-file"></a>構成ファイル

この要素は、アプリケーション構成ファイルで使用できます。

## <a name="see-also"></a>関連項目

- [スタートアップ設定スキーマ](../startup/index.md)
- [構成ファイル スキーマ](../index.md)
- [インプロセスの side-by-side 実行](../../../deployment/in-process-side-by-side-execution.md)
