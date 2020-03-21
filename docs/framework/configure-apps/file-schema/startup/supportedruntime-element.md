---
title: <supportedRuntime>構成要素 - .NET
ms.date: 04/02/2019
ms.custom: updateeachrelease
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime
helpviewer_keywords:
- supportedRuntime element
- <supportedRuntime> element
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
ms.openlocfilehash: e16eb098db4bce115a5f1e043829eb272c952860
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153699"
---
# <a name="supportedruntime-element"></a>\<サポートされているランタイム>要素

アプリケーションがサポートする共通言語ランタイムのバージョンと、必要に応じて .NET Framework のバージョンを指定します。  

[\<構成>](../configuration-element.md)  
&nbsp;&nbsp;[\<スタートアップ>](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<サポートされているランタイム>**  

## <a name="syntax"></a>構文

```xml
<supportedRuntime version="runtime version" sku="sku id"/>
```

## <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|**version**|省略可能な属性です。<br /><br /> このアプリケーションがサポートする共通言語ランタイム (CLR: Common Language Runtime) のバージョンを指定する文字列値。 `version`属性の有効な値については[、「ランタイム バージョン」の値](#version)セクションを参照してください。 **注:** NET Framework 3.5 を通じて、 "*ランタイム バージョン*" の値は*メジャー*の形式になります。*マイナー*.*をビルド*します。 .NET Framework 4 以降では、メジャー バージョン番号とマイナー バージョン番号 (つまり"v4.0.30319" ではなく "v4.0" ) のみが必要です。 短い文字列を使用することをお勧めします。|
|**Sku**|省略可能な属性です。<br /><br /> 在庫管理単位 (SKU) を指定する文字列の値。SKU はこのアプリケーションがサポートする .NET Framework リリースを指定します。<br /><br /> .NET Framework 4.0 以降では、`sku` 属性の使用が推奨されます。  この属性が指定される場合は、アプリケーションが対象とする .NET Framework のバージョンを示します。<br /><br /> sku 属性の有効な値については[、「sku id」の値](#sku)セクションを参照してください。|

## <a name="remarks"></a>解説

**\<サポートされているランタイム>** 要素がアプリケーション構成ファイルに存在しない場合は、アプリケーションのビルドに使用されるランタイムのバージョンが使用されます。

**\<サポートされているランタイム>** 要素は、バージョン 1.1 以降のランタイムを使用してビルドされたすべてのアプリケーションで使用する必要があります。 ランタイムのバージョン 1.0 のみをサポートするように構築されたアプリケーションは[\<、requiredRuntime>](../startup/requiredruntime-element.md)要素を使用する必要があります。

> [!NOTE]
> 構成ファイルを指定するために[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)関数を使用する場合は、ランタイム`<requiredRuntime>`のすべてのバージョンで要素を使用する必要があります。 要素`<supportedRuntime>`は、使用するときに無視[されます。](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
  
NET Framework 1.1 から 3.5 までのランタイムの複数のバージョンをサポートするアプリケーションでは、ランタイムの複数のバージョンをサポートする場合は、最初の要素で最も優先度の高いバージョンを指定し、最後の要素で最も優先度の低いバージョンを指定する必要があります。 NET Framework 4.0 以降のバージョンをサポートするアプリの`version`場合、属性は .NET Framework 4 以降のバージョンに共通する CLR`sku`バージョンを示し、属性はアプリが対象とする単一の .NET Framework バージョンを示します。

属性を**\<持つサポートされているランタイム>** 要素が構成ファイルに存在し、インストールされている .NET Framework のバージョンが低い場合、指定されたサポートされているバージョンの場合、アプリケーションの実行に失敗し、代わりにサポートされているバージョンをインストールするように求めるメッセージが表示されます。 `sku` それ以外の場合、アプリケーションはインストールされている任意のバージョンで実行しようとしますが、そのバージョンと完全に互換性がない場合は予期しない動作をすることがあります。 (.NET Framework のバージョン間の互換性の違いについては[、「.NET Framework でのアプリケーションの互換性](https://docs.microsoft.com/dotnet/framework/migration-guide/application-compatibility)」を参照してください)。したがって、エラー診断を容易にするため、アプリケーション構成ファイルにこの要素を含めすることをお勧めします。 (新しいプロジェクトの作成時に Visual Studio によって自動的に生成される構成ファイルには、その構成ファイルが既に含まれています)。
  
> [!NOTE]
> アプリケーションで[CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)などの従来のアクティブ化パスを使用し、それらのパスを以前のバージョンではなく CLR のバージョン 4 でアクティブ化する場合、またはアプリケーションが .NET Framework 4 でビルドされているが、以前のバージョンの .NET Framework でビルドされた混合モード アセンブリに依存している場合は、サポートされているランタイムの一覧で .NET Framework 4 を指定するだけでは不十分です。 さらに、構成ファイルの[\<スタートアップ>要素](../startup/startup-element.md)で、属性を`useLegacyV2RuntimeActivationPolicy`に設定する`true`必要があります。 ただし、この属性を`true`設定すると、以前のバージョンの .NET Framework でビルドされたすべてのコンポーネントは、ビルド時に使用されたランタイムではなく .NET Framework 4 を使用して実行されます。

アプリケーションは、そのアプリケーションを実行できる .NET Framework のすべてのバージョンでテストすることをお勧めします。

<a name="version"></a>
## <a name="runtime-version-values"></a>"ランタイム バージョン" の値
この`runtime`属性は、特定のアプリケーションに必要な共通言語ランタイム (CLR) のバージョンを指定します。 すべての .NET Framework v4.x バージョン`v4.0`が CLR を指定していることに注意してください。 次の表は、属性の*ランタイム バージョン*値の有効`version`な値を示しています。

|.NET Framework のバージョン|`version` 属性|
|----------------------------|-------------------------|
|1.0|"v1.0.3705"|
|1.1|"v1.1.4322"|
|2.0|"v2.0.50727"|
|3.0|"v2.0.50727"|
|3.5|"v2.0.50727"|
|4.0-4.8|"v4.0"|

## <a name="sku-id-values"></a><a name="sku"></a>"sku id" 値

この`sku`属性は、ターゲット フレームワーク モニカー (TFM) を使用して、アプリの実行を対象とし、実行する必要がある .NET Framework のバージョンを示します。 次の表は、.NET Framework 4`sku`以降、属性でサポートされている有効な値を示しています。

|.NET Framework のバージョン|`sku` 属性|
|----------------------------|---------------------|
|4.0|".NETFramework,Version=v4.0"|
|4.0、Client Profile|".NETFramework,Version=v4.0,Profile=Client"|
|4.0、プラットフォームの更新プログラム 1|".バージョン=v4.0.1"|
|4.0、Client Profile、更新プログラム 1|".バージョン=v4.0.1,プロファイル=クライアント"|
|4.0、プラットフォームの更新プログラム 2|".バージョン=v4.0.2"|
|4.0、Client Profile、更新プログラム 2|".バージョン=v4.0.2,プロファイル=クライアント"|
|4.0、プラットフォームの更新プログラム 3|".バージョン=v4.0.3"|
|4.0、Client Profile、更新プログラム 3|".バージョン=v4.0.3,プロファイル=クライアント"|
|4.5|".NETFramework,Version=v4.5"|
|4.5.1|".NETFramework,Version=v4.5.1"|
|4.5.2|".NETFramework,Version=v4.5.2"|
|4.6|".NETFramework,Version=v4.6"|
|4.6.1|".NETFramework,Version=v4.6.1"|
|4.6.2|".バージョン=v4.6.2"|
|4.7|".バージョン=v4.7"|
|4.7.1|".バージョン=v4.7.1"|
|4.7.2|".バージョン=v4.7.2"|
|4.8|".バージョン=v4.8"|

## <a name="example"></a>例

サポートされているランタイムのバージョンを構成ファイルで指定する例を次に示します。 構成ファイルは、アプリが .NET Framework 4.7 を対象としていることを示します。

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
