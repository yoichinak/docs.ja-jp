---
title: "方法 : UserControl クラスを継承する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5eec04e6122f32321c34efe030bfca943baed5bf
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>方法 : UserControl クラスを継承する
カスタム コードを使用して 1 つ以上の Windows フォーム コントロールの機能を組み合わせるには、"*ユーザー コントロール*" を作成します。 ユーザー コントロールは、迅速なコントロール開発、標準の Windows フォーム コントロールの機能、およびカスタム プロパティやカスタム メソッドの多用途性を組み合わせたものです。 ユーザー コントロールの作成を開始すると、デザイナーが表示され、標準の Windows フォーム コントロールを配置できます。 これらのコントロールは、標準コントロールの外観と動作 (ルック アンド フィール) に加えて、固有の機能のすべてを保持します。 ただし、これらのコントロールをユーザー コントロールに組み込んだ場合、コードを介して使用することはできなくなります。 ユーザー コントロールは独自の描画を行い、標準コントロールに関連付けられた基本的な機能もすべて処理します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### <a name="to-create-a-user-control"></a>ユーザー コントロールを作成するには  
  
1.  新しい **Windows コントロール ライブラリ** プロジェクトを作成します。  
  
     空白のユーザー コントロールを含む新しいプロジェクトが作成されます。  
  
2.  コントロールを、**ツールボックス**の **[Windows フォーム]** タブからデザイナーにドラッグします。  
  
3.  こうしたコントロールは、最終的なユーザー コントロールに表示するときと同じように、配置およびデザインする必要があります。 開発者が内在コントロールにアクセスできるようにするには、内在コントロールをパブリックとして宣言するか、内在コントロールを選択して公開します。 詳細については、「[方法: 内在コントロールのプロパティを公開する](../../../../docs/framework/winforms/controls/how-to-expose-properties-of-constituent-controls.md)」を参照してください。  
  
4.  コントロールに組み込むカスタム メソッドやカスタム プロパティを実装します。  
  
5.  F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。 詳細については、「[方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 [方法: コントロール クラスを継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-the-control-class.md)  
 [方法: 既存の Windows フォーム コントロールから継承する](../../../../docs/framework/winforms/controls/how-to-inherit-from-existing-windows-forms-controls.md)  
 [方法: Windows フォームのコントロールを作成する](../../../../docs/framework/winforms/controls/how-to-author-controls-for-windows-forms.md)  
 [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)  
 [方法: UserControl の実行時の動作をテストする](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md)
