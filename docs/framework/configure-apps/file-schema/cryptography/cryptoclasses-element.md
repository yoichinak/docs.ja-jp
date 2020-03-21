---
title: <cryptoClasses> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: c93fadf51297d59ab499e25de283700364903049
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155247"
---
# <a name="cryptoclasses-element"></a>\<クリプトクラス>要素
nameEntry 要素のフレンドリ名にマッピングされている暗号化クラスの一覧>含まれています。 [ \<](nameentry-element.md)  
  
[**\<構成>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<>**](mscorlib-element-for-cryptography-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<暗号化設定>**](cryptographysettings-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>名マッピング**](cryptonamemapping-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<暗号クラス>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<cryptoClasses>
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 [なし] :  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<暗号クラス>](cryptoclass-element.md)|** \<nameEntry>** 要素のフレンドリ名へのマッピングを持つ暗号化クラスが含まれています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号設定を含みます。|  
|`cryptoNameMapping`|表示名へのクラスのマッピングを含みます。|  
|`mscorlib`|要素を`cryptographySettings`格納します。|  
  
## <a name="example"></a>例  
 次の例は**\<、cryptoClass>** 要素を使用して暗号化クラスを参照し、ランタイムを構成する方法を示しています。 その後、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドに文字列 "RSA" を渡し、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>メソッドを使用して`MyCryptoRSAClass`オブジェクトを返します。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Security.Cryptography>
- [構成ファイル スキーマ](../index.md)
- [暗号化設定スキーマ](index.md)
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
- [暗号化.暗号化.クリプトネームを作成します。](xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A)
- [暗号化クラスの設定](../../configure-cryptography-classes.md)
