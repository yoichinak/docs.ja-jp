---
title: '方法: Windows フォーム上のオブジェクトをレイヤー化する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 8d0abbf0f71ac176d17261a0ae863938c575bdaf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59311663"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>方法: Windows フォーム上のオブジェクトをレイヤー化する
複雑なユーザー インターフェイスを作成またはマルチ ドキュメント インターフェイス (MDI) フォームを使用するときにコントロールと複雑なユーザー インターフェイス (UI) を作成する子フォームをレイヤーには多くの場合、します。 コントロールと windows グループのコンテキスト内での追跡に移動するには、z オーダーを操作します。 *Z オーダー* (深度) のフォームの z 軸に沿ってフォーム上のコントロールのビジュアル レイヤーが。 Z オーダーの上部にあるウィンドウには、その他のすべてのウィンドウが重複しています。 その他のすべての windows では、z オーダーの一番下にあるウィンドウが重複します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-layer-controls-at-design-time"></a>デザイン時にコントロールをレイヤーに  
  
1. レイヤー化コントロールを選択します。  
  
2. **形式**メニューで、**順序**、 をクリックし、**前面へ移動**または**背面へ**。  
  
### <a name="to-layer-controls-programmatically"></a>コントロールをプログラムでレイヤーを  
  
-   使用して、<xref:System.Windows.Forms.Control.BringToFront%2A>と<xref:System.Windows.Forms.Control.SendToBack%2A>コントロールの z オーダーを操作するメソッド。  
  
     たとえば場合、<xref:System.Windows.Forms.TextBox>コントロール、`txtFirstName`が下に別コントロールし、上部で、次のコードを使用します。  
  
    ```vb  
    txtFirstName.BringToFront()  
    ```  
  
    ```csharp  
    txtFirstName.BringToFront();  
    ```  
  
    ```cpp  
    txtFirstName->BringToFront();  
    ```  
  
> [!NOTE]
>  Windows フォームのサポート*コントロール コンテインメント*します。 コントロール コンテインメントの数などのコンテナー コントロール内のコントロールが配置<xref:System.Windows.Forms.RadioButton>内で制御する<xref:System.Windows.Forms.GroupBox>コントロール。 格納しているコントロール内のコントロールを重ねることができます。 グループ ボックスを移動すると、その内部に含まれているために同様に、コントロールが移動します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロール](index.md)
- [Windows フォームでのコントロールの配置](arranging-controls-on-windows-forms.md)
- [各 Windows フォーム コントロールのラベル設定とショートカットの作成](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
- [Windows フォーム コントロールの機能別一覧](windows-forms-controls-by-function.md)
