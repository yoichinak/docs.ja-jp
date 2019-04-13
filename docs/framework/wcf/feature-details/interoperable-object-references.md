---
title: 相互運用可能なオブジェクト参照
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 9cbbd5a34269a7c4a5c33d72487a02df21f2f0fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222706"
---
# <a name="interoperable-object-references"></a>相互運用可能なオブジェクト参照
既定では、<xref:System.Runtime.Serialization.DataContractSerializer> はオブジェクトを値でシリアル化します。 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> プロパティを使用すると、型のオブジェクトをシリアル化する場合に、オブジェクト参照を保持するようにデータ コントラクト シリアライザーに指示できます。  
  
## <a name="generated-xml"></a>生成される XML  
 例として、次のオブジェクトを考えます。  
  
```  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass   
{  
}  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `false` (既定値) に設定すると、次の XML が生成されます。  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> を `true` に設定すると、次の XML が生成されます。  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 ただし、<xref:System.Runtime.Serialization.XsdDataContractExporter> プロパティが `id` に設定されている場合でも、`ref` がそのスキーマに `preserveObjectReferences` 属性や `true` 属性を記述することはありません。  
  
## <a name="using-isreference"></a>IsReference の使用  
 スキーマの記述に従った有効なオブジェクト参照情報を生成するには、<xref:System.Runtime.Serialization.DataContractAttribute> 属性を型に適用し、<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> フラグを `true` に設定します。 前のサンプル クラス `IsReference` で `X` を使用するには、次のようにします。  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 次のような XML が生成されます。  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 `IsReference` を使用すると、メッセージのラウンド トリップに対応できます。 これを使用しない場合、型をスキーマから生成しても、その型に対して返された XML に、もともと想定していたスキーマとの互換性があるとは限りません。 つまり、`id` 属性と `ref` 属性がシリアル化されたとしても、元のスキーマによってこれらの属性 (またはすべての属性) が拒否される可能性があります。 `IsReference` をデータ メンバーに適用すれば、そのメンバーは、ラウンド トリップ時にも "参照可能" として認識され続けます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
