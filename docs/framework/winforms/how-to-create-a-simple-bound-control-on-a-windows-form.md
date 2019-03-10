---
title: '方法: Windows フォームに単純バインド コントロールを作成します。'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: f481b85c07a107b10d88d47c4873b555191bac7f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708341"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>方法: Windows フォームに単純バインド コントロールを作成します。
*単純バインディング*コントロールでデータセット テーブルの列の値などの 1 つのデータ要素を表示することができます。 できます単純にバインドするコントロールの任意のプロパティのデータ値にします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-simple-bind-a-control"></a>単純なコントロールをバインドする  
  
1.  データ ソースに接続します。 詳細については、次を参照してください。[データ ソースに接続する](../data/adonet/connecting-to-a-data-source.md)します。  
  
2.  フォームのコントロールを選択し、表示、**プロパティ**ウィンドウ。  
  
3.  展開、 **(DataBindings)** プロパティ。  
  
     最も頻繁にバインドされるプロパティは、下に表示されます、 **(DataBindings)** プロパティ。 たとえば、ほとんどのコントロールで、**テキスト**プロパティが最も頻繁にバインドされています。  
  
4.  たいプロパティのバインドが一般にバインドされるプロパティのいずれかをクリックして、**省略記号**ボタン (![VisualStudioEllipsesButton スクリーン ショット](./media/vbellipsesbutton.png "vbEllipsesButton")) で、 **(詳細)** ボックスを表示する、**フォーマットと詳細バインド**そのコントロールのプロパティの完全な一覧がダイアログ ボックス。  
  
5.  バインドし、下のドロップダウン矢印をクリックします。 プロパティを選択**バインド**します。  
  
     使用できるデータ ソースの一覧が表示されます。  
  
6.  目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。 たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。  
  
7.  バインド先の要素の名前をクリックします。  
  
8.  作業している場合、**フォーマットと詳細バインド**ダイアログ ボックスで、をクリックして **[ok]** に戻る、**プロパティ**ウィンドウ。  
  
9. コントロールの追加のプロパティをバインドする場合は、手順 3. ~ 7. を繰り返します。  
  
    > [!NOTE]
    >  単純バインド コントロールでは、1 つのデータ要素のみを表示するためには、Windows フォームに単純バインド コントロールにナビゲーション ロジックを含める非常に一般的です。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Binding>
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
- [データ連結と Windows フォーム](data-binding-and-windows-forms.md)
