---
title: '方法: デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 180fafa9ace5927fd84ec5dc0a1b2a342f771efd
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040025"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム コントロールを BindingSource コンポーネントにバインドする
フォームにコントロールを追加し、アプリケーションのユーザーインターフェイスを決定したら、コントロールをデータソースにバインドできます。これにより、ユーザーがアプリケーションに関連するデータを変更したり保存したりできるようになります。

 Windows フォームでコントロールまたは一連のコントロールをバインドすることは、フォーム<xref:System.Windows.Forms.BindingSource>上のコントロールとデータソースの間のブリッジとして、コントロールを使用すると最も簡単に実現できます。

 フォーム上の1つ以上のコントロールをデータにバインドできます。次の手順では、 <xref:System.Windows.Forms.TextBox>コントロールがデータソースにバインドされます。

 この手順を完了するには、データベースから派生したデータソースにバインドすることを前提としています。 他のデータストアからデータソースを作成する方法の詳細については、「[新しいデータソースの追加](/visualstudio/data-tools/add-new-data-sources)」を参照してください。

## <a name="to-bind-a-control-at-design-time"></a>デザイン時にコントロールをバインドするには

1. <xref:System.Windows.Forms.TextBox>コントロールをフォームにドラッグします。

2. **[プロパティ]** ウィンドウで、次のようにします。

    1. **[(連結)]** ノードを展開します。

    2. プロパティの<xref:System.Windows.Forms.TextBox.Text%2A>横にある矢印をクリックします。

         **DataSource** UI 型エディターが開きます。

         データソースが既にプロジェクトまたはフォーム用に構成されている場合は、そのデータソースが表示されます。

3. **[プロジェクト データ ソースの追加]** をクリックしてデータに接続し、データ ソースを作成します。

4. **データ ソース構成ウィザード**の開始ページで **[次へ]** をクリックします。

5. **[データソースの種類を選択]** ページで、 **[データベース]** を選択します。

6. **[データ接続の選択]** ページで、使用可能な接続の一覧からデータ接続を選択します。 目的のデータ接続が使用できない場合は、 **[新しい接続]** を選択して新しいデータ接続を作成します。

7. [**はい、接続を保存**します] を選択して、アプリケーション構成ファイルに接続文字列を保存します。

8. アプリケーションで使用するデータベース オブジェクトを選択します。 この場合、を表示<xref:System.Windows.Forms.TextBox>するテーブルのフィールドを選択します。

9. 必要な場合は、既定のデータセット名を変更します。

10. **[完了]** をクリックします。

11. **[プロパティ]** ウィンドウで、プロパティの<xref:System.Windows.Forms.TextBox.Text%2A>横にある矢印をもう一度クリックします。 **DataSource** UI 型エディターで、バインド先の<xref:System.Windows.Forms.TextBox>フィールドの名前を選択します。

     データ**ソース**UI 型エディターが閉じられ、データ<xref:System.Windows.Forms.BindingSource>セットと、そのデータ接続に固有のテーブルアダプターがフォームに追加されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [新しいデータ ソースの追加](/visualstudio/data-tools/add-new-data-sources)
- [データソースウィンドウ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
