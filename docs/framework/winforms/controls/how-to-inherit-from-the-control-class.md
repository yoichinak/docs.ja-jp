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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 02c40e310778bd476742f62ee8b9d8598b084a53
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015852"
---
# <a name="how-to-inherit-from-the-control-class"></a>方法: コントロール クラスを継承する

Windows フォームで使用する完全なカスタムコントロールを作成する場合は、 <xref:System.Windows.Forms.Control>クラスから継承する必要があります。 <xref:System.Windows.Forms.Control>クラスから継承する場合は、より多くの計画と実装を実行する必要がありますが、最大のオプションも用意されています。 から<xref:System.Windows.Forms.Control>継承する場合、コントロールを機能させるための非常に基本的な機能を継承します。 <xref:System.Windows.Forms.Control>クラスに固有の機能は、キーボードとマウスを使用してユーザー入力を処理し、コントロールの境界とサイズを定義し、windows ハンドルを提供し、メッセージの処理とセキュリティを提供します。 描画機能 (ここではコントロールのグラフィカル インターフェイスを実際に表示する機能) や、ユーザーとやり取りするための特定の機能は含まれていません。 このような機能はすべて、カスタム コードによって提供する必要があります。

## <a name="to-create-a-custom-control"></a>カスタム コントロールを作成するには

1. Visual Studio で、新しい**Windows アプリケーション**プロジェクトまたは**windows コントロールライブラリ**プロジェクトを作成します。

2. **[プロジェクト]** メニューの **[クラスの追加]** を選択します。

3. **[新しい項目の追加]** ダイアログ ボックスの **[カスタム コントロール]** をクリックします。

   新しいカスタム コントロールがプロジェクトに追加されます。

4. **F7**キーを押して、カスタムコントロールの**コードエディター**を開きます。

5. メソッドを探します。このメソッドは、基底クラスの<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドの呼び出しを除いて空になります。 <xref:System.Windows.Forms.Control.OnPaint%2A>

6. コントロールで使用するカスタム描画が組み込まれるように、コードを修正します。

   コントロールのグラフィックスをレンダリングするコードの記述については、「[コントロールのカスタム描画およびレンダリング](custom-control-painting-and-rendering.md)」を参照してください。

7. コントロールに組み込むカスタム メソッド、カスタム プロパティ、カスタム イベントを実装します。

8. コントロールを保存して、動作確認を行います。

## <a name="see-also"></a>関連項目

- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: UserControl クラスを継承する](how-to-inherit-from-the-usercontrol-class.md)
- [方法: 既存の Windows フォームコントロールから継承する](how-to-inherit-from-existing-windows-forms-controls.md)
- [方法: Windows フォームの作成者コントロール](how-to-author-controls-for-windows-forms.md)
- [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
