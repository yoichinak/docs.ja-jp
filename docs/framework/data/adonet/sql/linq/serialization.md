---
title: Serialization2
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a15ae411-8dc2-4ca3-84d2-01c9d5f1972a
ms.openlocfilehash: 1ff6f8b58e01c86ae1c1e2e1533b1997ba2eb6b0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742893"
---
# <a name="serialization"></a>シリアル化
このトピックで説明[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]シリアル化機能。 デザイン時のコード生成でシリアル化を追加する方法と、実行時の [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] のクラスのシリアル化の動作について説明します。  
  
 デザイン時には、次のいずれかの方法でシリアル化のコードを追加できます。  
  
- オブジェクト リレーショナル デザイナーで変更、**シリアル化モード**プロパティを**Unidirectional**します。  
  
- SQLMetal コマンドラインに追加、 **/serialization**オプション。 詳しくは、「[SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)」をご覧ください。  
  
## <a name="overview"></a>概要  
 によって生成されたコード[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]既定では、遅延読み込み機能を提供します。 遅延読み込みは、中間層でデータを必要に応じて透過的に読み込むうえでは非常に便利です。 しかし、シリアル化のときには問題です。遅延読み込みが意図されているかどうかに関係なく、シリアライザーによって遅延読み込みが発生するためです。 具体的には、オブジェクトがシリアル化されるときには、遅延読み込みされるすべての外部参照の推移的閉包がシリアル化されます。  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]シリアル化機能で主に 2 つのメカニズムを通じて、この問題に対応します。  
  
- <xref:System.Data.Linq.DataContext> のモードにより、遅延読み込みをオフにします (<xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A>)。 詳細については、「 <xref:System.Data.Linq.DataContext> 」を参照してください。  
  
- コード生成のスイッチにより、生成するエンティティに <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> 属性および <xref:System.Runtime.Serialization.DataMemberAttribute?displayProperty=nameWithType> 属性を生成します。 この方法と、シリアル化での遅延読み込みクラスの動作が、このトピックの主な話題です。  
  
### <a name="definitions"></a>定義  
  
- *DataContract シリアライザー*:既定の .NET Framework 3.0 またはそれ以降のバージョンの Windows Communication Framework (WCF) のコンポーネントによって使用されるシリアライザー。  
  
- *単方向シリアル化*:(循環を避けるため) には、一方向の関連付けプロパティのみが含まれるクラスのシリアル化されたバージョン。 慣例として、主キー/外部キーのリレーションシップの親側のプロパティをシリアル化の対象としてマークします。 双方向の関連付けの反対側はシリアル化しません。  
  
     [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、シリアル化の種類として、単方向シリアル化のみがサポートされています。  
  
## <a name="code-example"></a>コード例  
 次のコードは、Northwind サンプル データベースの典型的な `Customer` クラスおよび `Order` クラスを使用して、これらのクラスをシリアル化の属性で装飾するようすを示します。  
  
 [!code-csharp[DLinqSerialization#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#1)]
 [!code-vb[DLinqSerialization#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#1)]  
  
 [!code-csharp[DLinqSerialization#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#2)]
 [!code-vb[DLinqSerialization#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#2)]  
  
 [!code-csharp[DLinqSerialization#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#3)]
 [!code-vb[DLinqSerialization#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#3)]  
  
 次の例の `Order` クラスでは、簡略化のために、`Customer` クラスに関する逆関連付けのプロパティのみを示します。 循環参照を防ぐために、<xref:System.Runtime.Serialization.DataMemberAttribute> 属性はありません。  
  
 [!code-csharp[DLinqSerialization#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#4)]
 [!code-vb[DLinqSerialization#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#4)]  
  
 [!code-csharp[DLinqSerialization#5](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#5)]
 [!code-vb[DLinqSerialization#5](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#5)]  
  
### <a name="how-to-serialize-the-entities"></a>エンティティをシリアル化する方法  
 前のセクションで示したコードのエンティティは次のようにシリアル化できます。  
  
 [!code-csharp[DLinqSerialization#6](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/Program.cs#6)]
 [!code-vb[DLinqSerialization#6](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/Module1.vb#6)]  
  
### <a name="self-recursive-relationships"></a>自己再帰的リレーションシップ  
 自己再帰的リレーションシップも同じパターンに従います。 外部キーに関する関連付けのプロパティには <xref:System.Runtime.Serialization.DataMemberAttribute> 属性がなく、親プロパティにはあります。  
  
 次の 2 つの自己再帰的リレーションシップが存在するクラスを検討してください。Employee.Manager/Reports と employee.mentor/mentees です。  
  
 [!code-csharp[DLinqSerialization#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSerialization/cs/northwind-ser.cs#7)]
 [!code-vb[DLinqSerialization#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSerialization/vb/northwind-ser.vb#7)]  
  
## <a name="see-also"></a>関連項目

- [背景情報](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)
- [SqlMetal.exe (コード生成ツール)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md)
- [方法: エンティティをシリアル化可能にします。](../../../../../../docs/framework/data/adonet/sql/linq/how-to-make-entities-serializable.md)
