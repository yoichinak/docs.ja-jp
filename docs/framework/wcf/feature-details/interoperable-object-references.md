---
title: 相互運用可能なオブジェクト参照
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918971"
---
# <a name="interoperable-object-references"></a>相互運用可能なオブジェクト参照
既定では、<xref:System.Runtime.Serialization.DataContractSerializer>値でオブジェクトをシリアル化します。 使用することができます、<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>オブジェクトをシリアル化するときに、オブジェクト参照を保持するために、データ コントラクト シリアライザーに指示するプロパティ。  
  
## <a name="generated-xml"></a>生成される XML  
 例として、次のオブジェクトを考えます。  
  
```csharp  
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
   <B ref="1"></B>  
</X>  
```  
  
 ただし、<xref:System.Runtime.Serialization.XsdDataContractExporter>については説明しません、`id`と`ref`そのスキーマ内の属性場合でも、`preserveObjectReferences`プロパティに設定されて`true`します。  
  
## <a name="using-isreference"></a>IsReference の使用  
 スキーマの記述に従って有効なオブジェクト参照情報を生成するには、適用、<xref:System.Runtime.Serialization.DataContractAttribute>属性を型、および設定、<xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>フラグを`true`します。 次の例は、クラスを変更します`X`追加することで、前の例で`IsReference`:。  
  
```csharp
[DataContract(IsReference=true)]
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
````

 次のような XML が生成されます。  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 `IsReference` を使用すると、メッセージのラウンド トリップに対応できます。 これがない型がスキーマから生成されたときに、XML 出力の種類がもともと想定してスキーマを必ずしも互換性がないこと。 つまり、`id` 属性と `ref` 属性がシリアル化されたとしても、元のスキーマによってこれらの属性 (またはすべての属性) が拒否される可能性があります。 `IsReference`として認識されるように、メンバーは引き続きデータ メンバーに適用され、 *referenceable*ときにラウンドト リップできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
