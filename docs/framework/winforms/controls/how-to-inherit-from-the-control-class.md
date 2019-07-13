---
title: '方法: コントロール クラスを継承する'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 14f225f5587379b3efa7b6dc2475f1b697ebb281
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61941142"
---
# <a name="how-to-inherit-from-the-control-class"></a>方法: コントロール クラスを継承する
Windows フォームで使用する完全なカスタム コントロールを作成する場合から継承する必要があります、<xref:System.Windows.Forms.Control>クラス。 継承中に、<xref:System.Windows.Forms.Control>クラスは、多くの計画と実装を実行することは、オプションの最大範囲にも提供が必要です。 継承する場合<xref:System.Windows.Forms.Control>コントロールを動作を実現する非常に基本的な機能を継承します。 固有の機能、<xref:System.Windows.Forms.Control>クラス、キーボードとマウスによるユーザー入力の処理、コントロールのサイズと境界を定義します。、、windows ハンドルを提供しますおよびメッセージの処理とセキュリティを提供します。 描画機能 (ここではコントロールのグラフィカル インターフェイスを実際に表示する機能) や、ユーザーとやり取りするための特定の機能は含まれていません。 このような機能はすべて、カスタム コードによって提供する必要があります。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-create-a-custom-control"></a>カスタム コントロールを作成するには  
  
1. 新しい **Windows アプリケーション** プロジェクトまたは **Windows コントロール ライブラリ** プロジェクトを作成します。  
  
2. **[プロジェクト]** メニューの **[クラスの追加]** を選択します。  
  
3. **[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をクリックします。  
  
     新しいカスタム コントロールがプロジェクトに追加されます。  
  
4. F7 キーを押して、カスタム コントロールの**コード エディター**を開きます。  
  
5. 検索、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの呼び出しを除いて空白になります<xref:System.Windows.Forms.Control.OnPaint%2A>基本クラスのメソッド。  
  
6. コントロールで使用するカスタム描画が組み込まれるように、コードを修正します。  
  
     コントロールのグラフィックスをレンダリングするコードの記述については、「[コントロールのカスタム描画およびレンダリング](custom-control-painting-and-rendering.md)」を参照してください。  
  
7. コントロールに組み込むカスタム メソッド、カスタム プロパティ、カスタム イベントを実装します。  
  
8. コントロールを保存して、動作確認を行います。  
  
## <a name="see-also"></a>関連項目

- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: UserControl クラスを継承します。](how-to-inherit-from-the-usercontrol-class.md)
- [方法: 継承可能な既存の Windows フォーム コントロール](how-to-inherit-from-existing-windows-forms-controls.md)
- [方法: Windows フォームのコントロールの作成](how-to-author-controls-for-windows-forms.md)
- [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
