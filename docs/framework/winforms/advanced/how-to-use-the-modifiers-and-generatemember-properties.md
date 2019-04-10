---
title: '方法: Modifiers プロパティおよび GenerateMember プロパティを使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 6194ef288bd43267c2b00fa6d7c6250e90b37c75
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322642"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>方法: Modifiers プロパティおよび GenerateMember プロパティを使用する
2 つのプロパティが、デザイン環境によって提供される Windows フォームにコンポーネントを配置すると:`GenerateMember`と`Modifiers`します。 `GenerateMember`プロパティは、Windows フォーム デザイナーでコンポーネントのメンバー変数を生成するときを指定します。 `Modifiers`プロパティは、そのメンバー変数に割り当てられているアクセス修飾子。 場合の値、`GenerateMember`プロパティは`false`の値、`Modifiers`プロパティは影響を与えません。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a>コンポーネント フォームのメンバーであるかどうかを指定するには  
  
1. Windows フォーム デザイナーでフォームを開きます。  
  
2. 開く、**ツールボックス**、フォームで、3 つの配置と<xref:System.Windows.Forms.Button>コントロール。  
  
3. 設定、`GenerateMember`と`Modifiers`の各プロパティ<xref:System.Windows.Forms.Button>次の表に従ってコントロール。  
  
    |Button name|GenerateMember 値|修飾子の値|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|変更なし|  
  
4. ソリューションをビルドします。  
  
5. **ソリューション エクスプローラー**で、**[すべてのファイルを表示]** ボタンをクリックします。  
  
6. 開く、 **Form1**ノード、および、**コード エディター**、オープン、 **Form1.Designer.vb**または**Form1.Designer.cs**ファイル。 このファイルには、Windows フォーム デザイナーによって出力されるコードが含まれています。  
  
7. 3 つのボタンの宣言を探します。 次のコード例で指定された相違点を示しています、`GenerateMember`と`Modifiers`プロパティ。  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  既定では、Windows フォーム デザイナーによって、 `private` (`Friend` Visual basic) 修飾子などのコンテナー コントロールを<xref:System.Windows.Forms.Panel>します。 場合、ベース<xref:System.Windows.Forms.UserControl>または<xref:System.Windows.Forms.Form>がコンテナー コントロールでは、継承されたコントロールとフォーム内の新しい子を受け付けることができません。 ソリューションは、基本のコンテナー コントロールの修飾子を変更する`protected`または`public`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Button>
- [Windows フォームのビジュアルの継承](windows-forms-visual-inheritance.md)
- [チュートリアル: ビジュアル継承のデモンストレーション](walkthrough-demonstrating-visual-inheritance.md)
- [方法: Windows フォームを継承する](how-to-inherit-windows-forms.md)
