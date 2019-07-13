---
title: '方法: メソッドにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding to methods using ObjectDataProvider
- binding [WPF], to methods
- methods [WPF], binding to
ms.assetid: 5f55e71e-2182-42a0-88d1-700cc1427a7a
ms.openlocfilehash: 6cdad46fd6d9ef3bc4ce1a13fedb6ff1d639d93e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967844"
---
# <a name="how-to-bind-to-a-method"></a>方法: メソッドにバインドする
次の例を使用して、メソッドにバインドする方法を示しています。<xref:System.Windows.Data.ObjectDataProvider>します。  
  
## <a name="example"></a>例  
 この例では、`TemperatureScale` はメソッド `ConvertTemp` を持つクラスで、2 つのパラメーター (1 つは `double` でもう 1 つは `enum` 型 `TempType)`) を取得して、指定した値をある温度尺度から他の温度尺度へ変換します。 次の例では、<xref:System.Windows.Data.ObjectDataProvider>をインスタンス化するために使用、`TemperatureScale`オブジェクト。 `ConvertTemp` メソッドは、2 つの指定したパラメーターで呼び出されます。  
  
 [!code-xaml[BindToMethod#WindowResources](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#windowresources)]  
  
 このメソッドはリソースとして使用可能となり、その結果にバインドできます。 次の例では、<xref:System.Windows.Controls.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Controls.TextBox>と<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>の<xref:System.Windows.Controls.ComboBox>メソッドの 2 つのパラメーターにバインドされます。 これにより、ユーザーは、変換する温度と変換前の温度尺度を指定できます。 なお<xref:System.Windows.Data.Binding.BindsDirectlyToSource%2A>に設定されている`true`にバインドしているため、<xref:System.Windows.Data.ObjectDataProvider.MethodParameters%2A>のプロパティ、<xref:System.Windows.Data.ObjectDataProvider>インスタンスとによってラップされたオブジェクトのプロパティではなく、 <xref:System.Windows.Data.ObjectDataProvider> (、`TemperatureScale`オブジェクト)。  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> 、最後の<xref:System.Windows.Controls.Label>、ユーザーの内容を変更すると、更新、<xref:System.Windows.Controls.TextBox>または選択範囲の<xref:System.Windows.Controls.ComboBox>します。  
  
 [!code-xaml[BindToMethod#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/BindToMethod/CS/Window1.xaml#ui)]  
  
 コンバーター `DoubleToString` double 型の値を受け取り、文字列に変換されます、<xref:System.Windows.Data.IValueConverter.Convert%2A>方向 (バインディング ターゲットのバインディング ソースからは、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティ) に変換します、`string`を`double`で、 <xref:System.Windows.Data.IValueConverter.ConvertBack%2A>方向。  
  
 `InvalidationCharacterRule`は、<xref:System.Windows.Controls.ValidationRule>無効な文字を確認します。 赤色の枠線は、既定のエラー テンプレートの周囲、 <xref:System.Windows.Controls.TextBox>、入力値が double 値ではないときにユーザーに通知が表示されます。  
  
## <a name="see-also"></a>関連項目

- [方法トピック](data-binding-how-to-topics.md)
- [方法: 列挙値にバインドする](how-to-bind-to-an-enumeration.md)
