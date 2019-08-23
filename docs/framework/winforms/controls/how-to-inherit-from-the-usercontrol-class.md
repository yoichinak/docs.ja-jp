---
title: '方法: UserControl クラスを継承する'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
ms.openlocfilehash: 77233517203989f188a2b3ddf436656bc8da82a6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966564"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a>方法: UserControl クラスを継承する
カスタム コードを使用して 1 つ以上の Windows フォーム コントロールの機能を組み合わせるには、"*ユーザー コントロール*" を作成します。 ユーザー コントロールは、迅速なコントロール開発、標準の Windows フォーム コントロールの機能、およびカスタム プロパティやカスタム メソッドの多用途性を組み合わせたものです。 ユーザー コントロールの作成を開始すると、デザイナーが表示され、標準の Windows フォーム コントロールを配置できます。 これらのコントロールは、標準コントロールの外観と動作 (ルック アンド フィール) に加えて、固有の機能のすべてを保持します。 ただし、これらのコントロールをユーザー コントロールに組み込んだ場合、コードを介して使用することはできなくなります。 ユーザー コントロールは独自の描画を行い、標準コントロールに関連付けられた基本的な機能もすべて処理します。

## <a name="to-create-a-user-control"></a>ユーザー コントロールを作成するには

1. 新しい **Windows コントロール ライブラリ** プロジェクトを作成します。

     空白のユーザー コントロールを含む新しいプロジェクトが作成されます。

2. コントロールを、**ツールボックス**の **[Windows フォーム]** タブからデザイナーにドラッグします。

3. こうしたコントロールは、最終的なユーザー コントロールに表示するときと同じように、配置およびデザインする必要があります。 開発者が内在コントロールにアクセスできるようにするには、内在コントロールをパブリックとして宣言するか、内在コントロールを選択して公開します。 詳細については、「[方法: 内在コントロール](how-to-expose-properties-of-constituent-controls.md)のプロパティを公開します。

4. コントロールに組み込むカスタム メソッドやカスタム プロパティを実装します。

5. F5 キーを押してプロジェクトをビルドし、**UserControl Test Container** でコントロールを実行します。 詳細については、「[方法 :UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md)の実行時の動作をテストします。

## <a name="see-also"></a>関連項目

- [さまざまなカスタム コントロール](varieties-of-custom-controls.md)
- [方法: コントロールクラスから継承する](how-to-inherit-from-the-control-class.md)
- [方法: 既存の Windows フォームコントロールから継承する](how-to-inherit-from-existing-windows-forms-controls.md)
- [方法: Windows フォームの作成者コントロール](how-to-author-controls-for-windows-forms.md)
- [Visual Basic での継承されたイベント ハンドラーのトラブルシューティング](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [方法: UserControl の実行時の動作をテストする](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
