---
title: '方法: データベース リレーションシップを割り当てる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 538def39-8399-46fb-b02d-60ede4e050af
ms.openlocfilehash: 0637a2f32140081d310abf5f7254b526edc69fc6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743233"
---
# <a name="how-to-map-database-relationships"></a>方法: データベース リレーションシップを割り当てる
データ リレーションシップが常に同じ場合は、これをエンティティ クラス内のプロパティ参照としてエンコードできます。 たとえば、Northwind サンプル データベースでは、通常は顧客が注文を発注するため、モデルには、顧客と注文のリレーションシップが常に存在します。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 定義、<xref:System.Data.Linq.Mapping.AssociationAttribute>のため、このようなリレーションシップを表す属性です。 この属性を、<xref:System.Data.Linq.EntitySet%601> 型および <xref:System.Data.Linq.EntityRef%601> 型と共に使用することで、データベース内の外部キー リレーションシップが表されます。 詳細については、の「Association Attribute」セクションを参照してください。[属性ベースの対応付け](../../../../../../docs/framework/data/adonet/sql/linq/attribute-based-mapping.md)します。  
  
> [!NOTE]
>  AssociationAttribute プロパティ値と ColumnAttribute Storage プロパティ値では大文字と小文字が区別されます。 たとえば、AssociationAttribute.Storage  プロパティの属性に使用されている値は、コード内の別の場所で使用されている対応するプロパティ名と、大文字と小文字が一致するようにしてください。 これは、すべての .NET プログラミング言語も含めて通常小文字は区別されません、Visual Basic などに適用されます。 Storage プロパティの詳細については、「<xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A?displayProperty=nameWithType>」を参照してください。  
  
 ほとんどのリレーションシップは、このトピックの例のように、一対多のリレーションシップです。 次に示すように、一対一および多対多のリレーションシップも表すことができます。  
  
- 一対一。含めることによって、この種のリレーションシップを表す<xref:System.Data.Linq.EntitySet%601>両方の側でします。  
  
     たとえば、 `Customer` - `SecurityCode`作成されるため、お客様のセキュリティ コードが内に見つかりませんが、リレーションシップ、`Customer`テーブルし、承認されたユーザーのみアクセスできます。  
  
- 多対多:多対多リレーションシップのリンク テーブルの主キーで (とも呼ばれます、*接合*テーブル) の他の 2 つのテーブルから外部キーは、複合によって形式が多くの場合。  
  
     たとえば、 `Employee` - `Project`リンク テーブルを使用して形成された多対多のリレーションシップ`EmployeeProject`します。 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、このようなリレーションシップを、`Employee`、`Project`、および `EmployeeProject` という 3 つのクラスを使用してモデル化する必要があります。 この場合、`Employee` と `Project` の間のリレーションシップを変更すると、主キーの `EmployeeProject` の更新が必要であるように見える可能性がありす。 ただし、この状態は、既存の `EmployeeProject` の削除、および新しい `EmployeeProject` の作成として適切にモデル化されます。  
  
    > [!NOTE]
    >  リレーショナル データベース内のリレーションシップは、通常、他のテーブルの主キーを参照する外部キー値としてモデル化されます。 それらの間を移動するを明示的に 2 つのテーブルを使用して関連付けるリレーショナル*結合*操作。  
    >   
    >  内のオブジェクト[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]、他のプロパティ参照またはを使用して移動する参照のコレクションを使用して、互いを参照してください、渡す*ドット*表記します。  
  
## <a name="example"></a>例  
 次の一対多の例では、`Customer` クラスは、顧客とその注文のリレーションシップを宣言するプロパティを持ちます。  `Orders` プロパティは <xref:System.Data.Linq.EntitySet%601> 型です。 この型は、このリレーションシップが一対多 (1 人の顧客対多くの注文) であることを意味します。 <xref:System.Data.Linq.Mapping.AssociationAttribute.OtherKey%2A> プロパティを使用して、この関連付けを実現する方法を記述します。つまり、これと比較する、関連クラス内のプロパティの名前を指定します。 この例で、`CustomerID`データベースと同様、プロパティが比較*結合*その列の値を比較します。  
  
> [!NOTE]
>  Visual Studio を使用している場合は、クラス間の関連付けを作成するオブジェクト リレーショナル デザイナーを使用できます。  
  
 [!code-csharp[DlinqCustomize#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#3)]
 [!code-vb[DlinqCustomize#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#3)]  
  
## <a name="example"></a>例  
 逆の場合も可能です。 `Customer` クラスを使用して顧客と注文の関連付けを記述するのではなく、`Order` クラスを使用できます。 `Order` クラスは、<xref:System.Data.Linq.EntityRef%601> 型を使用して、次のコード例に示すように、顧客へのリレーションシップを記述できます。  
  
> [!NOTE]
>  <xref:System.Data.Linq.EntityRef%601>クラスでサポート*遅延読み込み*します。 詳細については、*を参照してください*[遅延読み込みと即時読み込み](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)します。  
  
 [!code-csharp[DLinqCustomize#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCustomize/cs/Program.cs#5)]
 [!code-vb[DLinqCustomize#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCustomize/vb/Module1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- [方法: コード エディターを使用してエンティティ クラスをカスタマイズします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)
- [LINQ to SQL オブジェクト モデル](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)
