---
title: <iriParsing> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 953d0b53-445e-41f9-b302-77c4030852ce
ms.openlocfilehash: 710d82b70eb16e88404d4d8bbf38d2d030693103
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092501"
---
# <a name="iriparsing-element-uri-settings"></a>\<iriParsing > 要素 (Uri 設定)
International Resource Identifier (IRI) 解析が、<xref:System.Uri> に適用されるかどうか、および IRI の解析規則が適用されるどうかを指定します。  
  
## <a name="schema-hierarchy"></a>スキーマの階層  
 [\<configuration > 要素](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Uri > 要素 (Uri 設定)](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
 [\<iriParsing >](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)  
  
## <a name="syntax"></a>構文  
  
```xml  
<iriParsing  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|`enabled`|解析する IRI が有効になっているかどうかを指定します。 既定値は `false` です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[uri](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)|.NET Framework での uniform resource identifier (Uri) を使用して表現された web アドレスの処理方法を指定する設定が含まれています。|  
  
## <a name="remarks"></a>Remarks  
 既存の<xref:System.Uri>クラスは、.NET Framework 3.5 で拡張されています。 3.0 SP1、および 2.0 SP1 国際リソース識別子 (IRI) および国際化ドメイン名 (IDN) のサポートを提供します。 IRI と IDN 明確には、現在のユーザーに、.NET Framework 2.0 の動作から変更は表示されないをサポートします。 これにより、.NET Framework の以前のバージョンとのアプリケーションの互換性を保証します。  
  
 IRI のサポートを有効にするのには、次の 2 つの変更が必要です。  
  
1.  .NET Framework 2.0 のディレクトリの machine.config ファイルに次の行を追加します。  
  
    ```xml  
    <section name="uri" type="System.Configuration.UriSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
    ```  
  
2.  IRI 解析規則を適用する必要があるかどうかを指定します。 これは、machine.config ファイルまたは app.config ファイルで指定できます。  
  
 IRI 解析を有効にする (iriParsing を有効になっている = `true`) 正規化を行うし、RFC 3987 ルール文字に従って最新の IRI チェックします。 既定値は`false`とは正規化を実行し、チェックに従って RFC 2396 および RFC 3986 を (IPv6 のリテラル) の文字します。  
  
### <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 次の例で使用する構成を示しています、<xref:System.Uri>解析する IRI と IDN 名をサポートするクラス。  
  
### <a name="code"></a>コード  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.IriParsingElement?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
