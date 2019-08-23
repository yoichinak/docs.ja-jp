---
title: <cryptoNameMapping> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: 87b24595f5013ad3b981256fd97bc758863c600b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921100"
---
# <a name="cryptonamemapping-element"></a>\<cryptoNameMapping > 要素
表示名へのクラスのマッピングを含みます。  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<cryptoNameMapping >  
  
## <a name="syntax"></a>構文  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|`cryptoClasses`|**\<nameEntry>** 要素内の表示名へのマッピングを持つ暗号化クラスのリストを含みます。|  
|`nameEntry`|アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号設定を含みます。|  
|`cryptoNameMapping`|表示名へのクラスのマッピングを含みます。|  
|`mscorlib`|Cryptographysettings > 要素を\<格納します。|  
  
## <a name="example"></a>例  
 次の例は、  **\<cryptoNameMapping >** 要素を使用して、暗号化クラスを参照し、ランタイムを構成する方法を示しています。 その後、文字列 "RSA" を<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドに渡し、 <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>メソッドを使用してオブジェクトを`MyCryptoRSAClass`返すことができます。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [構成ファイル スキーマ](../index.md)
- [暗号化設定スキーマ](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
- [暗号化クラスの設定](../../configure-cryptography-classes.md)
