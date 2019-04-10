---
title: '方法: デザイナーを使って Windows フォーム コントロールを型にバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: b298efb0494994659673f9bf9893b667f7eb0f8c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304214"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>方法: デザイナーを使って Windows フォーム コントロールを型にバインドする
データをやり取りするコントロールを作成する際、オブジェクトではなく型にコントロールをバインドすることが必要な場合があります。 データを使用できないが、データ バインド コントロールで型のパブリック インターフェイスからデータを表示する必要がある場合、通常はデザイン時にコントロールを型にバインドする必要があります。 次の手順を新規作成する方法を説明する<xref:System.Windows.Forms.BindingSource>は、型にバインドし、いずれかの型のプロパティにバインドする方法、<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティを<xref:System.Windows.Forms.TextBox>します。  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>BindingSource を型にバインドするには  
  
1. Windows フォーム プロジェクトの作成 (**ファイル** > **新規** > **プロジェクト** > **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**)。  
  
2. **デザイン**ビューで、ドラッグ、<xref:System.Windows.Forms.BindingSource>コンポーネントをフォームにします。  
  
3. **プロパティ**ウィンドウで、矢印をクリックして、<xref:System.Windows.Forms.BindingSource.DataSource%2A>プロパティ。  
  
4. **DataSource UI 型エディター**で、**[プロジェクト データ ソースの追加]** をクリックします。  
  
5. **[データ ソースの種類を選択]** ページで、**[オブジェクト]** を選択して **[次へ]** をクリックします。  
  
6. バインド先となる型を選択します。  
  
    -   バインド先となる型が現在のプロジェクトにある場合、または、型を含むアセンブリが参照として既に追加されている場合は、ノードを展開し、目的の型を探して選択します。  
  
         - または -  
  
    -   バインド先となる型が、現在、参照の一覧にはなく、別のアセンブリにある場合は、**[参照の追加]** をクリックして **[プロジェクト]** タブをクリックします。目的のビジネス オブジェクトを含むプロジェクトを選択して **[OK]** をクリックします。 このプロジェクトは、アセンブリの一覧に表示されるため、ノードを展開し、目的の型を探して選択します。  
  
        > [!NOTE]
        >  フレームワークまたは Microsoft アセンブリの型にバインドする場合は、**[Microsoft または System で始まるアセンブリを表示しない]** チェックボックスをオフにします。  
  
7. **[次へ]** をクリックし、 **[完了]** をクリックします。  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>コントロールを BindingSource にバインドするには  
  
1. フォームに <xref:System.Windows.Forms.TextBox> を追加します。  
  
2. **[プロパティ]** ウィンドウで **(DataBindings)** ノードを展開します。  
  
3. 矢印をクリックして、<xref:System.Windows.Forms.TextBox.Text%2A>プロパティ。  
  
4. **DataSource UI 型エディター**、ノードを展開、<xref:System.Windows.Forms.BindingSource>以前に追加しにバインドするバインドの型のプロパティを選択、<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティ、<xref:System.Windows.Forms.TextBox>します。  
  
## <a name="see-also"></a>関連項目

- [BindingSource コンポーネント](bindingsource-component.md)
- [方法: Windows フォーム コントロールを型にバインドする](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Visual Studio でのデータへのコントロールのバインド](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
