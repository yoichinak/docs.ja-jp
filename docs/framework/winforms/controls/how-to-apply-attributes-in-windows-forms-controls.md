---
title: '方法: Windows フォーム コントロールに属性を適用します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: fd41999b1cd1cde940d182f3acc505bbb92a3aa4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718546"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>方法: Windows フォーム コントロールに属性を適用します。
デザイン環境を正しく操作しを実行時に正しく実行するコンポーネントとコントロールを開発するには、クラスとメンバーに属性を正しく適用する必要があります。  
  
## <a name="example"></a>例  
 次のコード例では、カスタム コントロールでいくつかの属性を使用する方法を示します。 コントロールでは、単純なログ記録機能を示します。 コントロールがデータ ソースにバインドされると、内のデータ ソースから送信された値が表示されます、<xref:System.Windows.Forms.DataGridView>コントロール。 値で指定された値を超えた場合、`Threshold`プロパティ、`ThresholdExceeded`イベントが発生します。  
  
 `AttributesDemoControl`値をログに記録する`LogEntry`クラス。 `LogEntry`クラスは、ログを記録する型でパラメーター化されたことを意味するテンプレート クラスです。 たとえば場合、`AttributesDemoControl`型の値をログ記録は、 `float`、それぞれ`LogEntry`インスタンスが宣言され、次のように使用します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
>  `LogEntry`パラメーター化された任意の型によって、パラメーターの型を操作する、リフレクションを使用する必要がありますに。 しきい値機能するには、パラメーターの型を`T`実装する必要があります、<xref:System.IComparable>インターフェイス。  
  
 フォームをホストする、`AttributesDemoControl`パフォーマンス カウンターを定期的に照会します。 パッケージ化された各値を`LogEntry`適切な種類のフォームの追加と<xref:System.Windows.Forms.BindingSource>。 `AttributesDemoControl` 、データ バインディングを使用値を受け取っての値を表示、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 最初のコード例は、`AttributesDemoControl`実装します。 2 番目のコード例に示しますを使用する形式、`AttributesDemoControl`します。  
  
## <a name="class-level-attributes"></a>クラス レベルの属性  
 いくつかの属性は、クラス レベルで適用されます。 次のコード例では、一般的に、Windows フォーム コントロールに適用される属性を示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter 属性  
 <xref:System.ComponentModel.TypeConverterAttribute> 一般的に使用されるもう 1 つのクラス レベル属性です。 次のコード例の使用を示しています、`LogEntry`クラス。 この例では、実装も示しています、<xref:System.ComponentModel.TypeConverter>の`LogEntry`と呼ばれる型`LogEntryTypeConverter`します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>メンバー レベルの属性  
 いくつかの属性は、メンバー レベルで適用されます。 次のコード例では、一般的に Windows フォーム コントロールのプロパティに適用されるいくつかの属性を示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue 属性  
 次の例で、<xref:System.ComponentModel.AmbientValueAttribute>し、デザイン環境とのやり取りをサポートするコードを示しています。 この操作を呼び出す*アンビエンス*します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>データ バインド属性  
 次の例では、複合データ バインディングの実装を示します。 クラス レベル<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>のように、以前を指定します、`DataSource`と`DataMember`データ バインドに使用するプロパティ。 <xref:System.ComponentModel.AttributeProviderAttribute>対象の型を指定します、`DataSource`プロパティにバインドされます。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
-   フォームをホストする、`AttributesDemoControl`への参照が必要です、`AttributesDemoControl`アセンブリをビルドするためにします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [Windows フォーム コントロールの属性](attributes-in-windows-forms-controls.md)
- [方法: Designerserializationvisibilityattribute を使用、基本データ型のコレクションをシリアル化します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
