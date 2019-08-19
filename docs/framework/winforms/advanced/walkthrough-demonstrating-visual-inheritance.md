---
title: 'チュートリアル: ビジュアル継承のデモンストレーション'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 6fd504269ae9afbfd02b58276582a644674e1e0f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040319"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>チュートリアル: ビジュアル継承のデモンストレーション

ビジュアル継承により、基本フォームのコントロールを表示して、新しいコントロールを追加できます。 このチュートリアルでは、基本フォームを作成してクラス ライブラリにコンパイルします。 このクラス ライブラリを別のプロジェクトにインポートして、基本フォームから継承する新しいフォームを作成します。 このチュートリアルでは、次の作業を行う方法について説明します。

- 基本フォームを含むクラス ライブラリ プロジェクトを作成します。

- 基本フォームの派生クラスが変更できるプロパティを持つボタンを追加します。

- 基本フォームの継承元により変更できないボタンを追加します。

- `BaseForm` から継承したフォームを含むプロジェクトを作成します。

最終的には、このチュートリアルでは、継承されたフォーム上のプライベート コントロールとプロテクト コントロールの違いを示します。

> [!CAUTION]
> すべてのコントロールが基本フォームのビジュアル継承をサポートするわけではありません。 次のコントロールでは、このチュートリアルで説明するシナリオはサポートされません。
>
>  <xref:System.Windows.Forms.WebBrowser>
>
>  <xref:System.Windows.Forms.ToolStrip>
>
>  <xref:System.Windows.Forms.ToolStripPanel>
>
>  <xref:System.Windows.Forms.TableLayoutPanel>
>
>  <xref:System.Windows.Forms.FlowLayoutPanel>
>
>  <xref:System.Windows.Forms.DataGridView>
>
>  継承されたフォームのこれらのコントロールは、使用する修飾子 (`private`、`protected`、または `public`) に関係なく、常に読み取り専用です。

## <a name="create-a-class-library-project-containing-a-base-form"></a>基本フォームを含むクラスライブラリプロジェクトを作成する

1. Visual Studio で、[**ファイル**] メニューの [**新しい** > **プロジェクト**] をクリックし、[**新しいプロジェクト**] ダイアログボックスを開きます。

2. という名前`BaseFormLibrary`の Windows フォームアプリケーションを作成します。

3. 標準 Windows フォームアプリケーションではなくクラスライブラリを作成するには、**ソリューションエクスプローラー**で [ **baseformlibrary** ] プロジェクトノードを右クリックし、[**プロパティ**] を選択します。

4. プロジェクトのプロパティで、[**出力の種類**] を [ **Windows アプリケーション**] から [**クラスライブラリ**] に変更します。

5. [**ファイル**] メニューの [**すべてを保存**] をクリックして、プロジェクトとファイルを既定の場所に保存します。

 次の 2 つの手順では、基本フォームにボタンを追加します。 ビジュアル継承を示すには、`Modifiers` プロパティを設定して、ボタンに異なるアクセス レベルを付与します。

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a>基本フォームの継承元が変更できるボタンを追加します。

1. デザイナーで **Form1** を開きます。

2. **ツールボックス**の [**すべての Windows フォーム**] タブで、[ **] ボタン**をダブルクリックして、フォームにボタンを追加します。 マウスを使用し、ボタンを配置してサイズを変更します。

3. [プロパティ] ウィンドウで、ボタンの次のプロパティを設定します。

    - [ **Text** ] プロパティを「 **Hello**」に設定します。

    - **(Name)** プロパティを**btnprotected**に設定します。

    - **Modifiers**プロパティを**Protected**に設定します。 これにより、 **Form1**から継承するフォームが、 **btnprotected**のプロパティを変更できるようになります。

4. ダブルクリックして、 **Say こんにちは**のイベント ハンドラーを追加するボタン、 **をクリックして**イベント。

5. イベント ハンドラーに次のコードを追加します。

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>基本フォームの継承元によって変更できないボタンを追加する

1. クリックしてデザイン ビューに切り替え、 **Form1.vb [デザイン]、Form1.cs [デザイン]、または Form1.jsl の [デザイン]** コード エディターの上または F7 キーを押してタブです。

2. 2 番目のボタンを追加し、そのプロパティを次のように設定します。

    - Text プロパティを「」**と** **入力**します。

    - **(Name)** プロパティを**btnprivate**に設定します。

    - **Modifiers**プロパティを**Private**に設定します。 これにより、 **Form1**から継承したフォームでは、 **btnprivate**のプロパティを変更できなくなります。

3. ダブルクリックして、 **Say Goodbye**のイベント ハンドラーを追加するボタン、 **をクリックして**イベント。 イベントの手順で、次のコード行を配置します。

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. [**ビルド**] メニューの [ **Baseform library のビルド**] をクリックして、クラスライブラリをビルドします。

     ライブラリがビルドされたら、作成したフォームから継承する新しいプロジェクトを作成できます。

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>基本フォームから継承するフォームを含むプロジェクトを作成する

1. [**ファイル**] メニューの [**追加**] をポイントし、[**新しいプロジェクト**] をクリックして、[**新しいプロジェクトの追加**] ダイアログボックスを開きます。

2. という名前`InheritanceTest`の Windows フォームアプリケーションを作成します。

## <a name="add-an-inherited-form"></a>継承されたフォームを追加する

1. **ソリューションエクスプローラー**で、 **InheritanceTest**プロジェクトを右クリックし、[**追加**]、[**新しい項目**] の順に選択します。

2. [**新しい項目の追加**] ダイアログボックスで、[ **Windows フォーム**] カテゴリ (カテゴリの一覧がある場合) を選択し、[継承された**フォーム**] テンプレートを選択します。

3. 既定の`Form2`名前のままにして、[**追加**] をクリックします。

4. [**継承ピッカー** ] ダイアログボックスで、継承元のフォームとして**baseformlibrary**プロジェクトから**Form1**を選択し、[ **OK**] をクリックします。

     これにより、 **Baseformlibrary**のフォームから派生するフォームが**InheritanceTest**プロジェクトに作成されます。

5. デザイナーで、継承されたフォーム (**Form2**) をダブルクリックして開きます (まだ開いていない場合)。

     デザイナーでは、継承されたボタンにシンボル (![Visual Basic 継承シンボルのスクリーンショット。](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) を上隅に置いて、それらが継承されていることを示します。

6. [ **Hello Hello** ] ボタンを選択し、サイズ変更ハンドルを観察します。 このボタンは保護されているため、継承元が、移動、サイズ変更、キャプションの変更、およびその他の変更を実行できます。

7. [プライベート]ボタンをクリックし、サイズ変更ハンドルがないことを確認します。 また、[**プロパティ**] ウィンドウでは、このボタンのプロパティがグレーで表示され、変更できないことが示されています。

8. ビジュアルC#を使用している場合:

    1. **ソリューションエクスプローラー**で、 **InheritanceTest**プロジェクトの**Form1**を右クリックし、[**削除**] をクリックします。 表示されるメッセージボックスで、[ **OK** ] をクリックして削除を確定します。

    2. Program.cs ファイルを開き、行 `Application.Run(new Form1());` を `Application.Run(new Form2());` に変更します。

9. **ソリューションエクスプローラー**で、 **InheritanceTest**プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] を選択します。

10. **ソリューションエクスプローラー**で、 **InheritanceTest**プロジェクトを右クリックし、[**プロパティ**] を選択します。

11. **InheritanceTest**プロパティページで、 **Startup オブジェクト**を継承されたフォーム (**Form2**) に設定します。

12. **F5**キーを押してアプリケーションを実行し、継承されたフォームの動作を確認します。

## <a name="next-steps"></a>次の手順

ユーザー コントロールの継承はほぼ同じ方法で機能します。 新しいクラス ライブラリ プロジェクトを開き、ユーザー コントロールを追加します。 内在コントロールを配置し、プロジェクトをコンパイルします。 別の新しいクラス ライブラリ プロジェクトを開き、コンパイル済みのクラス ライブラリへの参照を追加します。 また、継承されたコントロールを ([**新しい項目の追加**] ダイアログボックスを使用して) プロジェクトに追加し、**継承ピッカー**を使用してみてください。 ユーザーコントロールを追加し、 `Inherits` (`:` Visual C#) ステートメントを変更します。 詳細については、「[方法 :Windows フォーム](how-to-inherit-windows-forms.md)を継承します。

## <a name="see-also"></a>関連項目

- [方法: Windows フォームを継承する](how-to-inherit-windows-forms.md)
- [Windows フォームのビジュアルの継承](windows-forms-visual-inheritance.md)
- [Windows フォーム](../index.md)
