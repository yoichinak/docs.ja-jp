---
title: '方法: データベース リレーションシップを割り当てる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: b6b1eba063c9ec72ae14c12028dd0950b2ad95f5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793524"
---
# <a name="how-to-map-database-relationships"></a>方法: データベース リレーションシップを割り当てる
データ リレーションシップが常に同じ場合は、これをエンティティ クラス内のプロパティ参照としてエンコードできます。 たとえば、Northwind サンプル データベースでは、通常は顧客が注文を発注するため、モデルには、顧客と注文のリレーションシップが常に存在します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]このようなリレーションシップを表すための属性を定義します。<xref:System.Data.Linq.Mapping.AssociationAttribute> この属性を、<xref:System.Data.Linq.EntitySet%601> 型および <xref:System.Data.Linq.EntityRef%601> 型と共に使用することで、データベース内の外部キー リレーションシップが表されます。 詳細については、「[属性ベースのマッピング](attribute-based-mapping.md)」の「Association 属性」セクションを参照してください。  
  
> [!NOTE]
> AssociationAttribute プロパティ値と ColumnAttribute Storage プロパティ値では大文字と小文字が区別されます。 たとえば、AssociationAttribute.Storage  プロパティの属性に使用されている値は、コード内の別の場所で使用されている対応するプロパティ名と、大文字と小文字が一致するようにしてください。 これは、Visual Basic など、通常は大文字と小文字が区別されないすべての .NET プログラミング言語に適用されます。 Storage プロパティの詳細については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>」を参照してください。  
  
 ほとんどのリレーションシップは、このトピックの例のように、一対多のリレーションシップです。 次に示すように、一対一および多対多のリレーションシップも表すことができます。  
  
- 1対 1:を両方の側に含める<xref:System.Data.Linq.EntitySet%601>ことで、この種類のリレーションシップを表します。  
  
     `Customer`たとえば、顧客の- セキュリティコード`SecurityCode`がテーブルで見つからず、承認されたユーザーのみがアクセスできるように作成されたリレーションシップを考えてみます。`Customer`  
  
- 多対多:多対多リレーションシップでは、リンクテーブルの主キー (*分岐点*テーブルとも呼ばれます) は、多くの場合、他の2つのテーブルの外部キーの複合として形成されます。  
  
     たとえば、 `Employee`リンクテーブル`Project` - を`EmployeeProject`使用して形成された多対多リレーションシップを考えてみます。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、このようなリレーションシップを、`Employee`、`Project`、および `EmployeeProject` という 3 つのクラスを使用してモデル化する必要があります。 この場合、`Employee` と `Project` の間のリレーションシップを変更すると、主キーの `EmployeeProject` の更新が必要であるように見える可能性がありす。 ただし、この状態は、既存の `EmployeeProject` の削除、および新しい `EmployeeProject` の作成として適切にモデル化されます。  
  
    > [!NOTE]
    > リレーショナル データベース内のリレーションシップは、通常、他のテーブルの主キーを参照する外部キー値としてモデル化されます。 これらの間を移動するには、リレーショナル*結合*操作を使用して、2つのテーブルを明示的に関連付けます。  
    >   
    >  一方、のオブジェクトは、ドット表記を使用して移動するプロパティ参照または参照のコレクションを使用して相互に参照します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
## <a name="example"></a>例  
 次の一対多の例では、`Customer` クラスは、顧客とその注文のリレーションシップを宣言するプロパティを持ちます。  `Orders` プロパティは <xref:System.Data.Linq.EntitySet%601> 型です。 この型は、このリレーションシップが一対多 (1 人の顧客対多くの注文) であることを意味します。 <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> プロパティを使用して、この関連付けを実現する方法を記述します。つまり、これと比較する、関連クラス内のプロパティの名前を指定します。 この例`CustomerID`では、データベース*結合*がその列の値を比較するのと同じように、プロパティが比較されます。  
  
> [!NOTE]
> Visual Studio を使用している場合は、オブジェクトリレーショナルデザイナーを使用して、クラス間の関連付けを作成できます。  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>例  
 逆の場合も可能です。 `Customer` クラスを使用して顧客と注文の関連付けを記述するのではなく、`Order` クラスを使用できます。 `Order` クラスは、<xref:System.Data.Linq.EntityRef%601> 型を使用して、次のコード例に示すように、顧客へのリレーションシップを記述できます。  
  
> [!NOTE]
> クラス<xref:System.Data.Linq.EntityRef%601>は、*遅延読み込み*をサポートしています。 詳細については、「[遅延読み込みと即時読み込み](deferred-versus-immediate-loading.md) *」を参照してください*。  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [方法: コードエディターを使用してエンティティクラスをカスタマイズする](how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL オブジェクト モデル](the-linq-to-sql-object-model.md)
