---
title: '方法: バインド コントロールを作成して表示データの書式を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 22ffdfcc1068dd546c8c07a481c9e21fb1faab80
ms.sourcegitcommit: 11deacc8ec9f229ab8ee3cd537515d4c2826515f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2019
ms.locfileid: "66003723"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>方法: バインド コントロールを作成して表示データの書式を設定する
Windows フォーム データ バインディングでは、データ バインド コントロールを使用して表示データの書式を設定することができます、**フォーマットと詳細バインド** ダイアログ ボックス。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>コントロールをバインドして表示データの書式を設定するには  
  
1. データ ソースに接続します。  
  
     詳細については、次を参照してください。[データ ソースに接続する](../data/adonet/connecting-to-a-data-source.md)します。  
  
2. フォームでコントロールを選択し、[プロパティ] ウィンドウを開きます。  
  
3.  展開、 **(DataBindings)** プロパティ、し、 **(詳細)** ボックスで、省略記号ボタンをクリックします (![Visual Studio の [プロパティ] ウィンドウで、省略記号ボタン (…).](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png))表示する、**フォーマットと詳細バインド**ダイアログ ボックスで、そのコントロールのプロパティの完全な一覧があります。  
  
4. クリックして、バインド プロパティを選択、**バインド**矢印。  
  
     使用できるデータ ソースの一覧が表示されます。  
  
5. 目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。  
  
     たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。  
  
6. バインド先の要素の名前をクリックします。  
  
7. **種類の形式を**ボックスに、コントロールに表示されるデータに適用する形式をクリックします。  
  
     どの形式でも、データ ソースに <xref:System.DBNull> が含まれている場合には、コントロールに表示する値を指定できます。 それ以外の場合、オプションは、選択する形式の種類に応じて多少変わります。 次の表に、形式の種類とオプションを示します。  
  
    |形式の種類|書式設定のオプション|  
    |-----------------|-----------------------|  
    |書式設定なし|オプションはありません。|  
    |数字|使用して小数点以下桁数を指定**小数点**アップダウン コントロール。|  
    |通貨|使用して小数点以下桁数を指定**小数点**アップダウン コントロール。|  
    |日付と時刻|日付と時刻を内の項目のいずれかを選択して表示する必要がある方法を選択、**型**選択ボックス。|  
    |指数|使用して小数点以下桁数を指定**小数点**アップダウン コントロール。|  
    |カスタム|カスタム書式指定文字列を使用するように指定します。<br /><br /> 詳細については、[型の書式設定](../../standard/base-types/formatting-types.md)に関するページをご覧ください。 **注:** カスタム書式指定文字列を使用した場合、データ ソースとバインド コントロールの間を往復したときにデータが正常に維持される保証はありません その代わりに、バインディングで <xref:System.Windows.Forms.Binding.Parse> イベントまたは <xref:System.Windows.Forms.Binding.Format> イベントを処理し、イベント処理コードでカスタム書式を適用します。|  
  
8. をクリックして**OK**を閉じる、**フォーマットと詳細バインド** ダイアログ ボックスと プロパティ ウィンドウに戻ります。  
  
## <a name="see-also"></a>関連項目

- [方法: Windows フォームに単純バインド コントロールを作成する](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows フォームでのユーザー入力の検証](user-input-validation-in-windows-forms.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
