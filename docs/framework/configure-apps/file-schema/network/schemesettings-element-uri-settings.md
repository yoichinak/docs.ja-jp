---
title: <schemeSettings> 要素 (Uri 設定)
ms.date: 03/30/2017
ms.assetid: 0ae45c6e-8c4c-4c0d-8b9f-a93824648890
ms.openlocfilehash: c745c90bb61b9ee393687d7f6db4fd11565c7dc7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154648"
---
# <a name="schemesettings-element-uri-settings"></a>\<schemeSettings> 要素 (Uri 設定)
<xref:System.Uri> が特定のスキームに解析される方法を指定します。  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<uri>**](uri-element-uri-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<スキーム設定>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<schemeSettings>
</schemeSettings>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[追加](add-element-for-schemesettings-uri-settings.md)|スキーム名のスキーム設定を追加します。|  
|[クリア](clear-element-for-schemesettings-uri-settings.md)|既存のスキーム設定をすべてクリアします。|  
|[削除](remove-element-for-schemesettings-uri-settings.md)|スキーム名のスキーム設定を削除します。|  
  
### <a name="parent-elements"></a>親要素  
  
|**Element**|**説明**|  
|-----------------|---------------------|  
|[Uri](uri-element-uri-settings.md)|統一リソース識別子 (URI) を使用して表される Web アドレスを .NET Framework が処理する方法を指定する設定が含まれています。|  
  
## <a name="remarks"></a>解説  
 既定では、クラス<xref:System.Uri?displayProperty=nameWithType>はパス圧縮を実行する前に、エンコードされたパスの区切り記号をパーセントでエスケープ解除します。 これは、次のような攻撃に対するセキュリティ メカニズムとして実装されました。  
  
 `http://www.contoso.com/..%2F..%2F/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 この URI がモジュールに渡されてパーセントエンコード文字が正しく処理されない場合、サーバーが実行するコマンドは次のようになります。  
  
 `c:\Windows\System32\cmd.exe /c dir c:\`  
  
 このため、class<xref:System.Uri?displayProperty=nameWithType>はまずパス区切り文字をアンエスケープし、次にパス圧縮を適用します。 上記の悪意のある URL をクラス<xref:System.Uri?displayProperty=nameWithType>コンストラクターに渡した結果、次の URI が生成されます。  
  
 `http://www.microsoft.com/Windows/System32/cmd.exe?/c+dir+c:\`  
  
 この既定の動作は、特定のスキームの schemeSettings 構成オプションを使用して、エンコードされたパス区切り記号をエスケープ解除しないように変更できます。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、http スキームの<xref:System.Uri>パーセントエンコードパス区切り記号をエスケープしないようにクラスで使用される構成を示しています。  
  
```xml  
<configuration>  
  <uri>  
    <schemeSettings>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="element-information"></a>要素情報  
  
|||
|-|-|  
|名前空間|システム|  
|スキーマ名||  
|検証ファイル||  
|空にできる||  
  
## <a name="see-also"></a>関連項目

- <xref:System.Configuration.SchemeSettingElement?displayProperty=nameWithType>
- <xref:System.Configuration.SchemeSettingElementCollection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection?displayProperty=nameWithType>
- <xref:System.Configuration.UriSection.SchemeSettings%2A?displayProperty=nameWithType>
- <xref:System.GenericUriParserOptions?displayProperty=nameWithType>
- <xref:System.Uri?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](index.md)
