---
title: プロパティ グリッドの拡張 - WF のサンプル
ms.date: 03/30/2017
ms.assetid: 3530c3a3-756d-4712-9f10-fb2897414d3a
ms.openlocfilehash: f1cb64cb10e8d88359e8f94b57602ab127314cff
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57509551"
---
# <a name="property-grid-extensibility"></a>プロパティ グリッドの拡張

開発者は、デザイナー内で特定のアクティビティを選択したときに表示されるプロパティ グリッドをカスタマイズできます。 これにより、高度な編集操作の作成が可能になります。 このサンプルでは、その方法を示します。

## <a name="demonstrates"></a>使用例

ワークフロー デザイナーのプロパティ グリッドの拡張。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`

## <a name="discussion"></a>説明

開発者がプロパティ グリッドを拡張できるように、プロパティ グリッド エディターのインラインの外観をカスタマイズするオプションと、高度な編集画面用のダイアログを表示するオプションが用意されています。 このサンプルでは、インライン エディターとダイアログ エディターの 2 種類のエディターを示します。

## <a name="inline-editor"></a>インライン エディター

インライン エディターのサンプルで示す内容は次のとおりです。

- 
  <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor> から派生する型を作成します。

- コンス トラクターで、 <xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> Windows Presentation Foundation (WPF) データ テンプレートを使用して値を設定します。 これは XAML テンプレートにバインドできますが、このサンプルではコードを使用してデータ バインディングを初期化します。

- プロパティ グリッドに表示される項目の <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> のデータ コンテキストは、データ テンプレートに含まれています。 次のコード (CustomInlineEditor.cs のコード) で、このコンテキストが `Value` プロパティにバインドされていることに注意してください。

    ```csharp
    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    FrameworkElementFactory slider = new FrameworkElementFactory(typeof(Slider));
    Binding sliderBinding = new Binding("Value");
    sliderBinding.Mode = BindingMode.TwoWay;
    slider.SetValue(Slider.MinimumProperty, 0.0);
    slider.SetValue(Slider.MaximumProperty, 100.0);
    slider.SetValue(Slider.ValueProperty, sliderBinding);
    stack.AppendChild(slider);
    ```

- アクティビティとデザイナーが同じアセンブリにあるため、アクティビティ デザイナーの属性の登録は、アクティビティ自体の静的コンストラクターで行われます。SimpleCodeActivity.cs の例を次に示します。

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="dialog-editor"></a>ダイアログ エディター

ダイアログ エディターのサンプルで示す内容は次のとおりです。

1. <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor> から派生する型を作成します。

2. コンストラクターで、<xref:System.Activities.Presentation.PropertyEditing.PropertyValueEditor.InlineEditorTemplate%2A> データ テンプレートを使用して [!INCLUDE[avalon2](../../../../includes/avalon2-md.md)] 値を設定します。 これは XAML で作成できますが、このサンプルではコードで作成します。

3. プロパティ グリッドに表示される項目の <xref:System.Activities.Presentation.PropertyEditing.PropertyValue> のデータ コンテキストは、データ テンプレートに含まれています。 次のコードで、これが `Value` プロパティにバインドされています。 FilePickerEditor.cs では、ダイアログを起動するボタンを指定するための <xref:System.Activities.Presentation.PropertyEditing.EditModeSwitchButton> を含めることも重要です。

    ```csharp
    this.InlineEditorTemplate = new DataTemplate();

    FrameworkElementFactory stack = new FrameworkElementFactory(typeof(StackPanel));
    stack.SetValue(StackPanel.OrientationProperty, Orientation.Horizontal);
    FrameworkElementFactory label = new FrameworkElementFactory(typeof(Label));
    Binding labelBinding = new Binding("Value");
    label.SetValue(Label.ContentProperty, labelBinding);
    label.SetValue(Label.MaxWidthProperty, 90.0);

    stack.AppendChild(label);

    FrameworkElementFactory editModeSwitch = new FrameworkElementFactory(typeof(EditModeSwitchButton));

    editModeSwitch.SetValue(EditModeSwitchButton.TargetEditModeProperty, PropertyContainerEditMode.Dialog);

    stack.AppendChild(editModeSwitch);

    this.InlineEditorTemplate.VisualTree = stack;
    ```

4. ダイアログの表示を処理するデザイナー型の <xref:System.Activities.Presentation.PropertyEditing.DialogPropertyValueEditor.ShowDialog%2A> メソッドをオーバーライドします。 このサンプルでは、基本的な <xref:System.Windows.Forms.FileDialog> を示します。

    ```csharp
    public override void ShowDialog(PropertyValue propertyValue, IInputElement commandSource)
    {
        Microsoft.Win32.OpenFileDialog ofd = new Microsoft.Win32.OpenFileDialog();
        if (ofd.ShowDialog() == true)
        {
            propertyValue.Value = ofd.FileName;
        }
    }
    ```

5. アクティビティとデザイナーが同じアセンブリにあるため、アクティビティ デザイナーの属性の登録は、アクティビティ自体の静的コンストラクターで行われます。SimpleCodeActivity.cs の例を次に示します。

    ```csharp
    static SimpleCodeActivity()
    {
        AttributeTableBuilder builder = new AttributeTableBuilder();
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "RepeatCount", new EditorAttribute(typeof(CustomInlineEditor), typeof(PropertyValueEditor)));
        builder.AddCustomAttributes(typeof(SimpleCodeActivity), "FileName", new EditorAttribute(typeof(FilePickerEditor), typeof(DialogPropertyValueEditor)));
        MetadataStore.AddAttributeTable(builder.CreateTable());
    }
    ```

## <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには

1. ソリューションをビルドし、Workflow1.xaml を開きます。

2. ドラッグ、 **SimpleCodeActivity**ツールボックスからデザイナー キャンバスにします。

3. をクリックして、 **SimpleCodeActivity**スライダー コントロールが、ファイル選択コントロールし、プロパティ グリッドを開きます。

> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\PropertyGridExtensibility`