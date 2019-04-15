---
title: <nameEntry> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 97521ba9073820beeea62f5fc7cab480b5422fb0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225327"
---
# <a name="nameentry-element"></a>\<nameEntry > 要素
アルゴリズムの表示名にクラス名をマップして、1 つのクラスが多くの表示名を持つことを許可します。  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings >  
\<cryptoNameMapping>  
\<nameEntry>  
  
## <a name="syntax"></a>構文  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**name**|必須の属性です。<br /><br /> 暗号化クラスを実装するアルゴリズムのフレンドリ名を指定します。|  
|**class**|必須の属性です。<br /><br /> 値を指定します、**名前**属性、 [ \<cryptoClass >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)要素。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`system.web`|ASP.NET 構成セクションのルート要素を指定します。|  
  
## <a name="remarks"></a>Remarks  
 **名前**属性は、抽象クラスのいずれかの名前を指定できます、<xref:System.Security.Cryptography>名前空間。 呼び出すと、**作成**抽象暗号化クラスのメソッドは、抽象クラスの名前に渡される、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>メソッド。 **CreateFromName**で示される型のインスタンスを返します、**クラス**属性。 場合、**名前**属性は、短い名前では、RSA などを呼び出すときに、その名前を使用できます、 **CreateFromName**メソッド。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、  **\<nameEntry >** 暗号化クラスを参照して、ランタイムを構成する要素。 文字列"RSA"を渡すことができますし、<xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType>メソッドを使用して、<xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A>を返すメソッドを`MyCryptoRSAClass`オブジェクト。  
  
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

- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [暗号設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [暗号化サービス](../../../../../docs/standard/security/cryptographic-services.md)
- [暗号化クラスの設定](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
