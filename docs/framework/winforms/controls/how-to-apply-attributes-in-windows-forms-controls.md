---
title: '方法: Windows フォーム コントロールに属性を適用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], applying attributes
- attributes [Windows Forms], applying
- Windows Forms controls, applying attributes
ms.assetid: af0a3f7f-155b-4ba1-83c4-9cf721331a06
ms.openlocfilehash: 273d32927582f4467a92cd3b8f87e699c1f167d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922793"
---
# <a name="how-to-apply-attributes-in-windows-forms-controls"></a>方法: Windows フォーム コントロールに属性を適用する
デザイン環境と正しく対話し、実行時に正常に実行されるコンポーネントとコントロールを開発するには、クラスおよびメンバーに属性を正しく適用する必要があります。  
  
## <a name="example"></a>例  
 次のコード例は、カスタムコントロールでいくつかの属性を使用する方法を示しています。 このコントロールは、単純なログ記録機能を示しています。 コントロールがデータソースにバインドされると、 <xref:System.Windows.Forms.DataGridView>コントロールにデータソースから送信された値が表示されます。 値が`Threshold`プロパティで指定された値を超えると`ThresholdExceeded` 、イベントが発生します。  
  
 は`AttributesDemoControl` 、クラスを`LogEntry`使用して値をログに記録します。 `LogEntry`クラスはテンプレートクラスであり、これはログに記録される型でパラメーター化されることを意味します。 たとえば、 `AttributesDemoControl`が型`float`の値をログに記録して`LogEntry`いる場合、各インスタンスは次のように宣言され、使用されます。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#110)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#110)]  
  
> [!NOTE]
> は`LogEntry`任意の型によってパラメーター化されるため、パラメーターの型を操作するにはリフレクションを使用する必要があります。 しきい値機能を機能させるには、 `T`パラメーターの型<xref:System.IComparable>がインターフェイスを実装する必要があります。  
  
 をホスト`AttributesDemoControl`するフォームは、パフォーマンスカウンターを定期的に照会します。 各値は、 `LogEntry`適切な型のにパッケージ化され、フォームの<xref:System.Windows.Forms.BindingSource>に追加されます。 は`AttributesDemoControl` 、データバインディングを通じて値を受け取り、 <xref:System.Windows.Forms.DataGridView>コントロールの値を表示します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#1)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#1)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/form1.cs#100)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/form1.vb#100)]  
  
 最初のコード例は`AttributesDemoControl` 、の実装です。 2番目のコード例は、 `AttributesDemoControl`を使用するフォームを示しています。  
  
## <a name="class-level-attributes"></a>クラスレベルの属性  
 一部の属性はクラスレベルで適用されます。 次のコード例は、Windows フォームコントロールに一般的に適用される属性を示しています。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#20)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#20)]  
  
### <a name="typeconverter-attribute"></a>TypeConverter 属性  
 <xref:System.ComponentModel.TypeConverterAttribute>は、一般的に使用されるもう1つのクラスレベルの属性です。 `LogEntry`クラスの使用例を次のコード例に示します。 この例では、という<xref:System.ComponentModel.TypeConverter> `LogEntry` `LogEntryTypeConverter`型のの実装も示しています。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#5)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#5)]  
  
## <a name="member-level-attributes"></a>メンバーレベルの属性  
 一部の属性は、メンバーレベルで適用されます。 次のコード例は、Windows フォームコントロールのプロパティに一般的に適用されるいくつかの属性を示しています。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#21)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#21)]  
  
### <a name="ambientvalue-attribute"></a>AmbientValue 属性  
 次の例は、 <xref:System.ComponentModel.AmbientValueAttribute>を示し、デザイン環境との対話をサポートするコードを示しています。 この相互作用は、"*アンビエント*" と呼ばれます。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#23)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#23)]  
  
### <a name="databinding-attributes"></a>Databinding 属性  
 次の例は、複合データバインディングの実装を示しています。 前に示した<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>クラスレベルでは、データ`DataSource`バインディング`DataMember`に使用するプロパティとプロパティを指定します。 は<xref:System.ComponentModel.AttributeProviderAttribute> 、 `DataSource`プロパティがバインドされる型を指定します。  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#25)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#25](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#25)]  
  
 [!code-csharp[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/CS/attributesdemocontrol.cs#26)]
 [!code-vb[System.ComponentModel.AttributesDemoControl#26](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AttributesDemoControl/VB/attributesdemocontrol.vb#26)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
  
- をホスト`AttributesDemoControl`するフォームは、ビルドするために`AttributesDemoControl`アセンブリへの参照を必要とします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IComparable>
- <xref:System.Windows.Forms.DataGridView>
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
- [Windows フォーム コントロールの属性](attributes-in-windows-forms-controls.md)
- [方法: DesignerSerializationVisibilityAttribute を使用して標準型のコレクションをシリアル化する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
