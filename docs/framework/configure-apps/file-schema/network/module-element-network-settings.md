---
title: <module> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154830"
---
# <a name="module-element-network-settings"></a>\<モジュール>要素(ネットワーク設定)
新しいプロキシ モジュールをアプリケーションに追加します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<既定のプロキシ>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<モジュール>**

## <a name="syntax"></a>構文  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`type`|プロキシを実装する<xref:System.Type.FullName%2A>完全修飾型名 (プロパティで示される) とアセンブリ名<xref:System.Reflection.Assembly.FullName%2A>(プロパティで示される名前)。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|ハイパーテキスト転送プロトコル (HTTP: Hypertext Transfer Protocol) プロキシ サーバーを構成します。|  
  
## <a name="remarks"></a>解説  
 要素`module`は、インターフェイスを実装するプロキシ<xref:System.Net.IWebProxy>クラスを登録します。 プロキシクラスを登録した後`module`、サポートされているプロキシを介して情報を要求するために使用できます。  
  
 属性の`type`値は、モジュールのクラス名と、対応するダイナミック リンク ライブラリ (DLL) の名前にする必要があります。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 カスタム プロキシ クラスを登録する例を次に示します。  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
