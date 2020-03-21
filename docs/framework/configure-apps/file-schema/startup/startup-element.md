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
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153733"
---
# <a name="startup-element"></a>\<スタートアップ>要素

共通言語ランタイムのスタートアップ情報を指定します。

[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;**\<スタートアップ>**  

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
|`useLegacyV2RuntimeActivationPolicy`|省略可能な属性です。<br /><br /> .NET Framework 2.0 ランタイム アクティベーション ポリシーを有効にするか、.NET Framework 4 のライセンス認証ポリシーを使用するかを指定します。|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a>属性を使用します。

|Value|説明|
|-----------|-----------------|
|`true`|選択したランタイムに対して .NET Framework 2.0 ランタイム アクティベーション ポリシーを有効にします。 [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) したがって、構成ファイルから CLR バージョン 4 以降を選択すると、以前のバージョンの .NET Framework で作成された混合モードアセンブリが、選択した CLR バージョンで読み込まれます。 この値を設定すると、CLR バージョン 1.1 または CLR バージョン 2.0 が同じプロセスに読み込まれるのを防ぎ、インプロセスのサイド バイ サイド機能を効果的に無効にします。|
|`false`|.NET Framework 4 以降の既定のアクティブ化ポリシーを使用すると、従来のランタイム アクティベーション手法で CLR バージョン 1.1 または 2.0 をプロセスに読み込むことができます。 この値を設定すると、.NET Framework 4 以降でビルドされていない限り、混在モードのアセンブリが .NET Framework 4 以降に読み込まれます。 この値は既定値です。|

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<必要なランタイム>](requiredruntime-element.md)|バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 ランタイム バージョン 1.1 以降でビルドされたアプリケーションは**\<、サポートされているランタイム>** 要素を使用する必要があります。|
|[\<サポートされているランタイム>](supportedruntime-element.md)|アプリケーションでサポートされる共通言語ランタイムのバージョンを指定します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|

## <a name="remarks"></a>解説

 **\<サポートされているランタイム>** 要素は、バージョン 1.1 以降のランタイムを使用してビルドされたすべてのアプリケーションで使用する必要があります。 ランタイムのバージョン 1.0 のみをサポートするように構築されたアプリケーションは**\<、requiredRuntime>** 要素を使用する必要があります。

 Internet Explorer でホストされているアプリケーションの**\<スタートアップ**コードは、スタートアップ>要素とその子要素を無視します。

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a>属性を使用します。

 この属性は、アプリケーションで[CorBindToRuntimeEx 関数](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)などの従来のアクティブ化パスを使用し、それらのパスを以前のバージョンではなく CLR のバージョン 4 をアクティブにする場合、またはアプリケーションが .NET Framework 4 でビルドされているが、以前のバージョンの .NET Framework でビルドされた混合モード アセンブリに依存している場合に便利です。 これらのシナリオでは、属性を に`true`設定します。

> [!NOTE]
> CLR バージョン`true`1.1 または CLR バージョン 2.0 が同じプロセスに読み込まれるのを防ぐために属性を設定し、インプロセスのサイド バイ サイド機能を効果的に無効に[します (COM 相互運用機能のサイド バイ サイド実行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))を参照)。

## <a name="example"></a>例

 次の例は、構成ファイルでランタイム バージョンを指定する方法を示しています。

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
- [方法: .NET Framework 4 以降のバージョンをサポートするようにアプリを構成する](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- [COM 相互運用機能の side-by-side 実行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))
- [インプロセスの side-by-side 実行](../../../deployment/in-process-side-by-side-execution.md)
