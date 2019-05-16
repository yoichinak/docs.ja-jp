---
title: <requiredRuntime> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: f5a9f99133c153401694372abaeea10a02e492e5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634193"
---
# <a name="requiredruntime-element"></a>\<requiredRuntime > 要素

バージョン 1.0 の共通言語ランタイムのみがアプリケーションでサポートされることを指定します。 この要素は非推奨し、使用できなくする必要があります。 [ `supportedRuntime` ](supportedruntime-element.md)要素を代わりに使用する必要があります。

\<configuration> \<startup> \<requiredRuntime>

## <a name="syntax"></a>構文

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|`version`|省略可能な属性です。<br /><br /> このアプリケーションがサポートする .NET Framework のバージョンを指定する文字列値。 文字列値は、.NET Framework のインストールのルート下にあるディレクトリ名と一致する必要があります。 文字列値の内容は解析されません。|
|`safemode`|省略可能な属性です。<br /><br /> ランタイム スタートアップ コードがランタイム バージョンを確認するレジストリを検索するかどうかを指定します。|

## <a name="safemode-attribute"></a>セーフ モード属性

|値|説明|
|-----------|-----------------|
|`false`|ランタイム スタートアップ コードは、レジストリを検索します。 これが既定値です。|
|`true`|ランタイム スタートアップ コードは、レジストリでは検索しません。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|
|`startup`|`<requiredRuntime>`要素を含んでいます。|

## <a name="remarks"></a>Remarks
 ランタイムのバージョン 1.0 をサポートするために構築されたアプリケーションを使用する必要があります、`<requiredRuntime>`要素。 1.1 以降、ランタイムのバージョンを使用して構築されたアプリケーションを使用する必要があります、`<supportedRuntime>`要素。

> [!NOTE]
> 使用する場合、 [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)構成ファイルを指定する関数を使用する必要があります、`<requiredRuntime>`ランタイムのすべてのバージョンの要素。 `<supportedRuntime>`を使用する場合、要素は無視されます[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)します。

 `version`属性文字列は指定されたバージョンの .NET Framework のインストール フォルダーの名前と一致する必要があります。 この文字列は解釈されません。 ランタイム スタートアップ コードが一致するフォルダーを見つけられない場合、ランタイムが読み込まれていません。スタートアップ コードでは、エラー メッセージが表示され、終了します。

> [!NOTE]
> Microsoft Internet Explorer でホストされているアプリケーションのスタートアップ コードは無視されます、`<requiredRuntime>`要素。

## <a name="example"></a>例

次の例では、構成ファイルでランタイムのバージョンを指定する方法を示します。

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>関連項目

- [スタートアップ設定スキーマ](index.md)
- [構成ファイル スキーマ](../index.md)
- [方法: .NET Framework 4 以降のバージョンをサポートするアプリを構成する](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
