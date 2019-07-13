---
title: 暗号化アルゴリズムへのオブジェクト ID の割り当て
ms.date: 03/30/2017
helpviewer_keywords:
- digital signatures
- identifiers, mapping object identifiers
- cryptographic algorithms
- mapping object identifiers
- cryptography, mapping object identifiers
ms.assetid: c9673f81-bf9e-47fd-bc6f-6bc1c1c4c15e
ms.openlocfilehash: e035ff04a70a441f7f64bbc230ba6d8036fb2ace
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775779"
---
# <a name="mapping-object-identifiers-to-cryptography-algorithms"></a>暗号化アルゴリズムへのオブジェクト ID の割り当て
データが 1 つのプログラムから別の送信時いない改ざんデジタル署名を確認します。 通常、デジタル署名がハッシュに署名するデータの数学関数を適用することによって計算されます。 署名のハッシュ値を書式設定時に、一部のデジタル署名アルゴリズムは、書式設定操作の一部として ASN.1 オブジェクト識別子 (OID) を追加します。 OID は、ハッシュを計算に使用されたアルゴリズムを識別します。 アルゴリズムは、カスタム アルゴリズムを使用する暗号化メカニズムを拡張するオブジェクトの識別子にマップできます。 次の例では、新しいハッシュ アルゴリズムにオブジェクト識別子をマップする方法を示します。  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass MyNewHash="MyNewHashClass, MyAssembly  
                  Culture='en', PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="NewHash" class="MyNewHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.14.33.42.46"  name="NewHash"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
 [ \<OidEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)2 つの属性が含まれています。 **OID**属性は、オブジェクトの識別番号。 **名前**属性の値が、**名前**属性を[ \<nameEntry > 要素](../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)します。 オブジェクト識別子は、簡易名にマップできる前に、アルゴリズム名からクラスへのマッピングする必要があります。  
  
## <a name="see-also"></a>関連項目

- [暗号化クラスの設定](../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [Cryptographic Services](../../../docs/standard/security/cryptographic-services.md)
