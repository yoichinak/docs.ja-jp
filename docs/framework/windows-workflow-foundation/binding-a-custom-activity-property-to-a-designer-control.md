---
title: デザイナー コントロールへのカスタム アクティビティ プロパティのバインド
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 142a9eb273a98d3a2d83a1239d6d7c891d5cc305
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468573"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>デザイナー コントロールへのカスタム アクティビティ プロパティのバインド

テキスト ボックスのデザイナー コントロールをアクティビティ引数にバインドする方法はきわめて簡単ですが、コンボ ボックスなどの複合デザイナー コントロールをアクティビティ引数にバインドする場合は困難が伴うことがあります。 このトピックでは、カスタム アクティビティ デザイナーでアクティビティ引数をコンボ ボックス コントロールにバインドする方法について説明します。

## <a name="creating-the-combo-box-item-converter"></a>コンボ ボックス項目コンバーターの作成

1. Visual Studio で、CustomProperty という名前で新しい空のソリューションを作成します。

2. ComboBoxItemConverter という名前で新しいクラスを作成します。 System.Windows.Data に参照を追加し、<xref:System.Windows.Data.IValueConverter> の派生クラスを使用できるようにします。 Visual Studio で、`Convert` および `ConvertBack` のスタブを生成するインターフェイスを実装します。

3. `Convert` メソッドに次のコードを追加します。 次のコードはアクティビティの <xref:System.Activities.InArgument%601> 型の <xref:System.String> をデザイナーに配置される値に変換します。

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (vbexpression != null)
            {
                return vbexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

     上のコード スニペットの式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> の代わりに <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用しても作成できます。

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            CSharpValue<string> csexpression = expression as CSharpValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (csexpression != null)
            {
                return csexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

4. `ConvertBack` メソッドに次のコードを追加します。 このコードは受信コンボ ボックス項目を <xref:System.Activities.InArgument%601> に戻します。

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     上のコード スニペットの式は、<xref:Microsoft.CSharp.Activities.CSharpValue%601> の代わりに <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> を使用しても作成できます。

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>アクティビティのカスタム デザイナーへの ComboBoxItemConverter の追加

1. 新しい項目をプロジェクトに追加します。 [新しい項目] ダイアログ ボックスで [ワークフロー] ノードを選択し、新しい項目の種類として [アクティビティ デザイナー] を選択します。 項目に CustomPropertyDesigner という名前を付けます。

2. 新しいデザイナーにコンボ ボックスを追加します。 Items プロパティには、コンボ ボックスに 2 つの項目を追加し、コンテンツの値に "Item1" および "Item2" を指定します。

3. コンボ ボックスの XAML を変更し、新しい項目コンバーターをコンボ ボックスに使用する項目コンバーターとして追加します。 コンバーターは ActivityDesigner.Resources セグメントにリソースとして追加され、<xref:System.Windows.Controls.ComboBox> の Converter 属性にコンバーターを指定します。 プロジェクトの名前空間はアクティビティ デザイナーの名前空間属性で指定します。デザイナーを別のプロジェクトで使用する場合は、この名前空間を変更する必要があります。

    ```xaml
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:c="clr-namespace:CustomProperty"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">

        <sap:ActivityDesigner.Resources>
            <ResourceDictionary>
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>
            </ResourceDictionary>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">
                <ComboBoxItem>item1</ComboBoxItem>
                <ComboBoxItem>item2</ComboBoxItem>
            </ComboBox>
        </Grid>
    </sap:ActivityDesigner>
    ```

4. <xref:System.Activities.CodeActivity> 型の新しい項目を作成します。 この例では、アクティビティの IDE によって作成された既定のコードで十分です。

5. クラス定義に次の属性を追加します。

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     この行は、新しいデザイナーを新しいクラスに関連付けます。

 これで新しいアクティビティがデザイナーに関連付けられました。 新しいアクティビティをテストするには、アクティビティをワークフローに追加し、コンボ ボックスに 2 つの値を設定します。 プロパティ ウィンドウが更新されてコンボ ボックスの値が反映されます。
