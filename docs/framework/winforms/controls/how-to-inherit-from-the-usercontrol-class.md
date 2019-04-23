---
title: '方法: UserControl クラスを継承する'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 5e9bdb6d6628b1c696b7944dc0ea1f4c974c8172
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311410"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>方法: UserControl クラスを継承する
カスタム コードを使用して 1 つ以上の Windows フォーム コントロールの機能を組み合わせるには、"*ユーザー コントロール*" を作成します。 ユーザー コントロールは、迅速なコントロール開発、標準の Windows フォーム コントロールの機能、およびカスタム プロパティやカスタム メソッドの多用途性を組み合わせたものです。 ユーザー コントロールの作成を開始すると、デザイナーが表示され、標準の Windows フォーム コントロールを配置できます。 これらのコントロールは、標準コントロールの外観と動作 (ルック アンド フィール) に加えて、固有の機能のすべてを保持します。 ただし、これらのコントロールをユーザー コントロールに組み込んだ場合、コードを介して使用することはできなくなります。 ユーザー コントロールは独自の描画を行い、標準コントロールに関連付けられた基本的な機能もすべて処理します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-a-user-control"></a>ユーザー コントロールを作成するには  
  
1. 新しい **Windows コントロール ライブラリ** プロジェクトを作成します。  
  
     空白のユーザー コントロールを含む新しいプロジェクトが作成されます。  
  
2. コントロールを、**ツールボックス**の **[Windows フォーム]** タブからデザイナーにドラッグします。  
  
3. こうしたコントロールは、最終的なユーザー コントロールに表示するときと同じように、配置およびデザインする必要があります。 開発者が内在コントロールにアクセスできるようにするには、内在コントロールをパブリックとして宣言するか、内在コントロールを選択して公開します。 詳細については、「[方法: 内在コントロールのプロパティを公開](how-to-expose-properties-of-constituent-controls.md)します。  
  
4. コントロールに組み込むカスタム メソッドやカスタム プロパティを実装します。  
  
5. F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。 詳細については、「[方法 :UserControl の実行時の動作をテスト](how-to-test-the-run-time-behavior-of-a-usercontrol.md)します。  
  
## <a name="see-also"></a>関連項目

- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: コントロール クラスから継承します。](how-to-inherit-from-the-control-class.md)
- [方法: 継承可能な既存の Windows フォーム コントロール](how-to-inherit-from-existing-windows-forms-controls.md)
- [方法: Windows フォームのコントロールの作成](how-to-author-controls-for-windows-forms.md)
- [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [方法: UserControl の実行時の動作をテストします。](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
