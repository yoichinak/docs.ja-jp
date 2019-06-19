---
title: <startup> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: 022f0efbbb2e6e9a4ac9d3d7ddcc1fb1022cdbee
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169769"
---
# <a name="startup-element"></a>\<startup> 要素

共通言語ランタイムのスタートアップの情報を指定します。

 \<configuration> \<startup>

## <a name="syntax"></a>構文

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a>属性と要素

 以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|省略可能な属性です。<br /><br /> .NET Framework 2.0 ランタイムのアクティブ化ポリシーを有効にする、または .NET Framework 4 のアクティブ化ポリシーを使用するかどうかを指定します。|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>useLegacyV2RuntimeActivationPolicy 属性

|値|説明|
|-----------|-----------------|
|`true`|レガシ ランタイムのアクティブ化の手法をバインドするには、選択したランタイムの .NET Framework 2.0 ランタイムのアクティブ化ポリシーを有効にする (など、 [CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md))、ランタイムの代わりに、構成ファイルから選択するにはCLR バージョン 2.0 では、それらを上限します。 したがって、CLR バージョン 4 以降を構成ファイルから選択した場合、.NET Framework の以前のバージョンで作成された混合モードのアセンブリは、選択した CLR バージョンで読み込まれます。 この値の設定も、実質的にインプロセスでサイド バイ サイドでの機能を無効にする、同じプロセスに読み込みの CLR バージョン 1.1 または CLR バージョン 2.0 はできません。|
|`false`|レガシの実行時に CLR 1.1 または 2.0 バージョンを読み込むプロセスのアクティブ化の手法を許可する、.NET Framework 4 以降では、既定のアクティブ化のポリシーを使用します。 この値を設定すると、混合モードのアセンブリから、またはそれ以降、.NET Framework 4 でビルドされた場合を除きに、.NET Framework 4 またはそれ以降の読み込みができません。 この値が既定値です。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 ランタイム バージョン 1.1 以降でビルドされたアプリケーションを使用する必要があります、  **\<supportedRuntime >** 要素。|
|[\<supportedRuntime>](supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|

## <a name="remarks"></a>Remarks

 **\<SupportedRuntime >** 1.1 以降、ランタイムのバージョンを使用して構築されたすべてのアプリケーションで要素を使用する必要があります。 ランタイムのバージョン 1.0 をサポートするために構築されたアプリケーションを使用する必要があります、  **\<requiredRuntime >** 要素。

 Microsoft Internet Explorer でホストされるアプリケーションのスタートアップ コードは無視されます、 **\<スタートアップ >** 要素とその子要素。

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>UseLegacyV2RuntimeActivationPolicy 属性

 この属性は、アプリケーションなどに、レガシ アクティブ化パスを使用する場合に便利ですが、 [CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)、それらのパスを以前のバージョンではなく、CLR の version 4 をアクティブ化して、アプリケーションがある場合、またはビルドされた .NET Framework 4、.NET Framework の以前のバージョンでビルドされた混合モードのアセンブリに依存しています。 そのようなシナリオで、属性を設定して`true`します。

> [!NOTE]
> 属性を設定`true`CLR version 1.1 または CLR バージョン 2.0 が実質的にインプロセスでサイド バイ サイドでの機能を無効にする、同じプロセスに読み込まれなくなります (を参照してください[COM 相互運用機能のサイド バイ サイドで実行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100)))。

## <a name="example"></a>例

 次の例では、構成ファイルでランタイムのバージョンを指定する方法を示します。

```xml
<!-- When used with version 1.0 of the .NET Framework runtime -->
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
<!-- When used with version 1.1 (or later) of the runtime -->
<configuration>
   <startup>
      <supportedRuntime version="v1.1.4322"/>
      <supportedRuntime version="v1.0.3705"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>関連項目

- [スタートアップ設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM 相互運用機能のサイド バイ サイドで実行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [インプロセスの side-by-side 実行](../../../deployment/in-process-side-by-side-execution.md)
