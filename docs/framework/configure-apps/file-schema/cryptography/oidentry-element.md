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
ms.openlocfilehash: c686d2b99ad66aec753a356b09fa3c7151193808
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219344"
---
# <a name="oidentry-element"></a>\<oidEntry > 要素
ASN.1 オブジェクト識別子 (OID) を表示名にマップします。  
  
 \<configuration>  
\<mscorlib>  
\<cryptographySettings >  
\<oidMap>  
\<oidEntry>  
  
## <a name="syntax"></a>構文  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**OID**|必須の属性です。<br /><br /> クラスで実装されているアルゴリズムに対応する ASN.1 OID を指定します。|  
|**name**|必須の属性です。<br /><br /> 値を指定します、**名前**属性、 [ \<nameEntry >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)タグ。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`cryptographySettings`|暗号設定を含みます。|  
|`mscorlib`|`cryptographySettings`要素を含んでいます。|  
|`oidMap`|クラスへの ASN.1 オブジェクト識別子 (OID) のマッピングが含まれています。|  
  
## <a name="remarks"></a>Remarks  
 ASN.1 オブジェクト識別子では、いくつかの暗号化形式でアルゴリズムを識別します。 オブジェクト識別子を特定するアルゴリズムの表示名にマップします。  
  
## <a name="example"></a>例  
 次の例は、使用する方法を示します、  **\<oidEntry >** ripemd-160 のハッシュ アルゴリズムのオブジェクト識別子をそのハッシュ アルゴリズムの実装にマップする要素。  
  
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

- [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [暗号設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [暗号化サービス](../../../../../docs/standard/security/cryptographic-services.md)
- [暗号化クラスの設定](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [暗号化アルゴリズムへのオブジェクト ID の割り当て](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
