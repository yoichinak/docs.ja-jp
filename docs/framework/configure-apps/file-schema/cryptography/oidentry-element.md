---
title: <oidEntry> 要素
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: 013994e36c4c63410a753967cbac92c38783ae62
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659586"
---
# <a name="oidentry-element"></a>\<oidEntry > 要素
ASN.1 オブジェクト識別子 (OID) を表示名にマップします。  
  
 \<configuration>  
\<mscorlib >  
\<cryptographySettings >  
\<oidMap>  
\<oidEntry >  
  
## <a name="syntax"></a>構文  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**ドーナツ**|必須の属性です。<br /><br /> クラスによって実装されたアルゴリズムに対応する asn.1 OID を指定します。|  
|**name**|必須の属性です。<br /><br /> Nameentry > タグの**name**属性[の値を指定します。 \<](nameentry-element.md)|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号設定を含みます。|  
|`mscorlib`|`cryptographySettings`要素を含んでいます。|  
|`oidMap`|クラスに対する asn.1 オブジェクト識別子 (OID) マッピングが含まれています。|  
  
## <a name="remarks"></a>Remarks  
 Asn.1 オブジェクト識別子は、一部の暗号化形式でアルゴリズムを識別します。 オブジェクト識別子を、識別するアルゴリズムのフレンドリ名にマップします。  
  
## <a name="example"></a>例  
 次の例は、  **\<oidEntry >** 要素を使用して、RIPEMD 160 ハッシュアルゴリズムのオブジェクト識別子をそのハッシュアルゴリズムの実装にマップする方法を示しています。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- [構成ファイル スキーマ](../index.md)
- [暗号化設定スキーマ](index.md)
- [Cryptographic Services](../../../../../docs/standard/security/cryptographic-services.md)
- [暗号化クラスの設定](../../configure-cryptography-classes.md)
- [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../map-object-identifiers-to-cryptography-algorithms.md)
