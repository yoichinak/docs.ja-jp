---
title: '方法: デザイナーを使って Windows フォーム コントロールを型にバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 5069d7d3b5ef4c5b05159dac521d32f5be8abdd1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046038"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>方法: デザイナーを使って Windows フォーム コントロールを型にバインドする

データをやり取りするコントロールを作成する際、オブジェクトではなく型にコントロールをバインドすることが必要な場合があります。 データを使用できないが、データ バインド コントロールで型のパブリック インターフェイスからデータを表示する必要がある場合、通常はデザイン時にコントロールを型にバインドする必要があります。 次の手順では、型にバインド<xref:System.Windows.Forms.BindingSource>される新しいを作成する方法と、型のプロパティの1つをの<xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.Windows.Forms.TextBox>プロパティにバインドする方法について説明します。

### <a name="to-bind-the-bindingsource-to-a-type"></a>BindingSource を型にバインドするには

1. Windows フォームプロジェクトを作成します ([**ファイル** > ] [**新しい** > **プロジェクト** > ] **[ビジュアルC# ]** または [ **Visual Basic** > **クラシックデスクトップ** > ] **Windows フォームアプリケーション**)。

2. **デザイン**ビューで、コンポーネントを<xref:System.Windows.Forms.BindingSource>フォームにドラッグします。

3. **[プロパティ]** ウィンドウで、 <xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティの矢印をクリックします。

4. **DataSource UI 型エディター**で、 **[プロジェクト データ ソースの追加]** をクリックします。

5. **[データ ソースの種類を選択]** ページで、 **[オブジェクト]** を選択して **[次へ]** をクリックします。

6. バインド先となる型を選択します。

    - バインド先となる型が現在のプロジェクトにある場合、または、型を含むアセンブリが参照として既に追加されている場合は、ノードを展開し、目的の型を探して選択します。

      \- または -

    - バインド先となる型が、現在、参照の一覧にはなく、別のアセンブリにある場合は、 **[参照の追加]** をクリックして **[プロジェクト]** タブをクリックします。目的のビジネス オブジェクトを含むプロジェクトを選択して **[OK]** をクリックします。 このプロジェクトは、アセンブリの一覧に表示されるため、ノードを展開し、目的の型を探して選択します。

      > [!NOTE]
      > フレームワークまたは Microsoft アセンブリの型にバインドする場合は、 **[Microsoft または System で始まるアセンブリを表示しない]** チェックボックスをオフにします。

7. **[次へ]** をクリックし、 **[完了]** をクリックします。

### <a name="to-bind-the-control-to-the-bindingsource"></a>コントロールを BindingSource にバインドするには

1. フォームに <xref:System.Windows.Forms.TextBox> を追加します。

2. **[プロパティ]** ウィンドウで **(DataBindings)** ノードを展開します。

3. プロパティの<xref:System.Windows.Forms.TextBox.Text%2A>横にある矢印をクリックします。

4. **DataSource UI 型エディター**で、前に追加し<xref:System.Windows.Forms.BindingSource>たのノードを展開し、の<xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.Windows.Forms.TextBox>プロパティにバインドするバインドされた型のプロパティを選択します。

## <a name="see-also"></a>関連項目

- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: Windows フォームコントロールを型にバインドする](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
