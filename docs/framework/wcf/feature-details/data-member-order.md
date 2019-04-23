---
title: データ メンバーの順序
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data contracts [WCF], ordering members
ms.assetid: 0658a47d-b6e5-4ae0-ba72-ababc3c6ff33
ms.openlocfilehash: c78cc682c0776bfb0ce09dec7ba1ff8cab504285
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59198570"
---
# <a name="data-member-order"></a>データ メンバーの順序
一部のアプリケーションでは、各種のデータ メンバーから送信される、または受信されると予想できるデータの順序 (たとえばシリアル化された XML でデータが表れる順序) がわかると便利です。 この順序を変更する必要が生じることもあります。 ここでは、このような順序を決定する規則について説明します。  
  
## <a name="basic-rules"></a>基本的な規則  
 データの順序を決定する基本的な規則には、次のようなものがあります。  
  
-   データ コントラクト型が継承階層の一部である場合、その基本型のデータ メンバーが常に最初の順番になります。  
  
-   次に来るのは <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティが設定されていない、現在の型のデータ メンバー (アルファベット順) になります。  
  
-   その次に来るのは、<xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> 属性の <xref:System.Runtime.Serialization.DataMemberAttribute> プロパティが設定されているすべてのデータ メンバーです。 これらのデータ メンバーはまず `Order` プロパティの値によって並べられ、次に特定の `Order` 値を持つメンバーが複数ある場合は、そのアルファベット順に並びます。 Order 値はスキップされることがあります。  
  
 アルファベット順は、<xref:System.String.CompareOrdinal%2A> メソッドを呼び出すことによって確立されます。  
  
## <a name="examples"></a>使用例  
 次のコードについて考えてみましょう。  
  
 [!code-csharp[C_DataContractNames#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractnames/cs/source.cs#4)]
 [!code-vb[C_DataContractNames#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractnames/vb/source.vb#4)]  
  
 作成される XML は、次のようになります。  
  
```xml  
<DerivedType>  
    <!-- Zebra is a base data member, and appears first. -->  
    <zebra/>   
  
    <!-- Cat has no Order, appears alphabetically first. -->  
    <cat/>  
  
   <!-- Dog has no Order, appears alphabetically last. -->  
    <dog/>   
  
    <!-- Bird is the member with the smallest Order value -->  
    <bird/>  
  
    <!-- Albatross has the next Order value, alphabetically first. -->  
    <albatross/>  
  
    <!-- Parrot, with the next Order value, alphabetically last. -->  
     <parrot/>  
  
    <!-- Antelope is the member with the highest Order value. Note that   
    Order=2 is skipped -->  
     <antelope/>   
</DerivedType>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractAttribute>
- [データ コントラクトの等価性](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)
- [データ コントラクトの使用](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
