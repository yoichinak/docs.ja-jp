---
title: '方法: バインド コントロールを作成して表示データの書式を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: b5ad85a9477ca32cd28f246abe4ece3cace43182
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666781"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>方法: バインド コントロールを作成して表示データの書式を設定する

Windows フォームデータバインディングでは、 **[書式設定と詳細バインド]** ダイアログボックスを使用して、データバインドコントロールに表示されるデータの書式を設定できます。

### <a name="to-bind-a-control-and-format-the-displayed-data"></a>コントロールをバインドして表示データの書式を設定するには

1. データ ソースに接続します。

     詳細については、「[データソースへの接続](../data/adonet/connecting-to-a-data-source.md)」を参照してください。

2. フォームでコントロールを選択し、[プロパティ] ウィンドウを開きます。

3. **[(連結)]** プロパティを展開し、 **[(詳細)]** ボックスで、省略記号ボタン![(Visual Studio のプロパティウィンドウの省略記号ボタン ([...]](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) をクリックして、**書式設定と詳細設定を表示します。[バインド**] ダイアログボックス。このダイアログボックスには、そのコントロールのプロパティの完全な一覧が表示されます。

4. バインドするプロパティを選択し、 **[バインド]** 矢印をクリックします。

     使用できるデータ ソースの一覧が表示されます。

5. 目的の 1 つのデータ要素が見つかるまで、バインド先のデータ ソースを展開します。

     たとえば、データセットのテーブル内の列の値にバインドする場合は、データセットの名前を展開し、次にテーブル名を展開して、列名を表示します。

6. バインド先の要素の名前をクリックします。

7. **[形式の種類]** ボックスで、コントロールに表示されるデータに適用する形式をクリックします。

     どの形式でも、データ ソースに <xref:System.DBNull> が含まれている場合には、コントロールに表示する値を指定できます。 それ以外の場合、オプションは、選択する形式の種類に応じて多少変わります。 次の表に、形式の種類とオプションを示します。

    |形式の種類|書式設定のオプション|
    |-----------------|-----------------------|
    |書式設定なし|オプションはありません。|
    |数字|小数点**以下**の桁数をアップダウンコントロールで指定します。|
    |通貨|小数点**以下**の桁数をアップダウンコントロールで指定します。|
    |日付と時刻|[**種類**の選択] ボックスでいずれかの項目を選択して、日付と時刻を表示する方法を選択します。|
    |指数|小数点**以下**の桁数をアップダウンコントロールで指定します。|
    |カスタム|カスタム書式指定文字列を使用するように指定します。<br /><br /> 詳細については、[型の書式設定](../../standard/base-types/formatting-types.md)に関するページをご覧ください。 **注:** カスタム書式指定文字列を使用した場合、データ ソースとバインド コントロールの間を往復したときにデータが正常に維持される保証はありません その代わりに、バインディングで <xref:System.Windows.Forms.Binding.Parse> イベントまたは <xref:System.Windows.Forms.Binding.Format> イベントを処理し、イベント処理コードでカスタム書式を適用します。|

8. **[OK]** をクリックして **[書式設定と詳細バインド]** ダイアログボックスを閉じ、プロパティウィンドウに戻ります。

## <a name="see-also"></a>関連項目

- [方法: Windows フォームに単純バインド コントロールを作成する](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Windows フォームでのユーザー入力の検証](user-input-validation-in-windows-forms.md)
- [Windows フォームでのデータ バインディング](windows-forms-data-binding.md)
