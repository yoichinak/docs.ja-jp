---
title: '方法: 継承階層を割り当てる'
ms.date: 03/30/2017
ms.assetid: b27c779b-9355-4dc7-b95f-7dfd504b6e48
dev_langs:
- csharp
- vb
ms.openlocfilehash: 618abc8e681a6f43a1054d0ca2cec2fbdec853f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943573"
---
# <a name="how-to-map-inheritance-hierarchies"></a>方法: 継承階層を割り当てる
[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] で継承の割り当てを実装するには、以下の手順で示すように、継承階層のルート クラスで属性および属性プロパティを指定する必要があります。 Visual Studio を使用する開発者は、オブジェクトリレーショナルデザイナーを使用して継承階層をマップできます。 「[方法:O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)」を参照してください。  
  
> [!NOTE]
> サブクラスには特別な属性やプロパティは必要ありません。 特に、サブクラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性がない点に注意してください。  
  
### <a name="to-map-an-inheritance-hierarchy"></a>継承階層を割り当てるには  
  
1. ルート クラスに <xref:System.Data.Linq.Mapping.TableAttribute> 属性を追加します。  
  
2. ルート クラスに対し、階層構造の各クラスについて <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性を追加します。  
  
3. 各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> プロパティを定義します。  
  
     このプロパティは、データベース テーブルの <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 列に含まれる値を保持し、このデータ行が属するクラスまたはサブクラスを示します。  
  
4. 各 <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性に対し、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Type%2A> プロパティも追加します。  
  
     このプロパティは、キー値が示すクラスまたはサブクラスを表す値を保持します。  
  
5. 1 つの <xref:System.Data.Linq.Mapping.InheritanceMappingAttribute> 属性にのみ、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.IsDefault%2A> プロパティを追加します。  
  
     このプロパティは、データベーステーブルの識別子の値が継承マッピングのどの<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A>値とも一致しない場合に、フォールバックマッピングを指定するために機能します。  
  
6. <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDiscriminator%2A> 属性に <xref:System.Data.Linq.Mapping.ColumnAttribute> プロパティを追加します。  
  
     このプロパティは、<xref:System.Data.Linq.Mapping.InheritanceMappingAttribute.Code%2A> 値を保持する列であることを示します。  
  
## <a name="example"></a>例  
  
> [!NOTE]
> Visual Studio を使用している場合は、オブジェクトリレーショナルデザイナーを使用して継承を構成できます。 「[方法:O/R デザイナーを使用して継承を構成する](/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer)  
  
 次のコード例では、`Vehicle` をルート クラスとして定義し、ここまでの手順を実装して、[!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] の階層構造を指定します。  
  
 [!code-csharp[DLinqCustomize#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#4)]
 [!code-vb[DLinqCustomize#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [継承のサポート](../../../../../../docs/framework/data/adonet/sql/linq/inheritance-support.md)
- [方法: コードエディターを使用してエンティティクラスをカスタマイズする](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
