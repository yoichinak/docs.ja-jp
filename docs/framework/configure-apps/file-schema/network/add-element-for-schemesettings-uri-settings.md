---
title: schemeSettings の <add> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 594a7b3b-af23-4cfa-b616-0b2dddb1a705
ms.openlocfilehash: 027c7aaffea7950739f532309255d77afa031ada
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659555"
---
# <a name="add-element-for-schemesettings-uri-settings"></a>\<schemeSettings (Uri 設定) の > 要素の追加
スキーム名のスキーム設定を追加します。  
  
 \<configuration>  
\<uri>  
\<schemeSettings>  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add
  name="http|https"
  genericUriParserOptions="DontUnescapePathDotsAndSlashes"
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|name|この設定を適用するスキーム名。 サポートされている値は、name = "http" と name = "https" だけです。|  
  
## <a name="attribute-name-attribute"></a>{属性名}属性  
  
|[値]|説明|  
|-----------|-----------------|  
|genericUriParserOptions|このスキームのパーサーオプション。 サポートされている値は、genericUriParserOptions = "DontUnescapePathDotsAndSlashes" だけです。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<schemeSettings> 要素 (Uri 設定)](schemesettings-element-uri-settings.md)|<xref:System.Uri> が特定のスキームに解析される方法を指定します。|  
  
## <a name="remarks"></a>Remarks  
 既定では、 <xref:System.Uri?displayProperty=nameWithType>クラスは、パスの圧縮を実行する前に、エンコードされたパス区切り記号のエスケープを解除します。 これは、次のような攻撃に対するセキュリティメカニズムとして実装されています。  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 % Encoded 文字を正しく処理しないモジュールにこの URI が渡された場合、サーバーによって次のコマンドが実行される可能性があります。  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 このため、クラス<xref:System.Uri?displayProperty=nameWithType>はまずパスの区切り記号をエスケープ解除し、次にパスの圧縮を適用します。 上の悪意のある URL をクラスコンストラクター <xref:System.Uri?displayProperty=nameWithType>に渡すと、次の URI が生成されます。  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、パーセントエンコードされたパス区切り記号のエスケープを解除しないように変更できます。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、http スキームに対し<xref:System.Uri>てパーセントでエンコードされたパス区切り記号をエスケープしないようにするために、クラスによって使用される構成を示しています。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
