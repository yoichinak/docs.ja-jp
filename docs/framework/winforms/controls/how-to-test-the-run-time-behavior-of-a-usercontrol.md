---
title: '方法: UserControl の実行時の動作をテストする'
ms.date: 03/30/2017
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1be79d52be3b5b84938d8548a8f101e965fa9dbb
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015776"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>方法: UserControl の実行時の動作をテストする

を開発<xref:System.Windows.Forms.UserControl>するときは、実行時の動作をテストする必要があります。 別個の Windows ベースのアプリケーションプロジェクトを作成し、テストフォームにコントロールを配置することはできますが、この手順は不便です。 Visual Studio によって提供される**UserControl テストコンテナー**を使用する方が、より高速で簡単な方法です。 このテストコンテナーは、Windows コントロールライブラリプロジェクトから直接開始します。

> [!IMPORTANT]
> テストコンテナーでを読み込む<xref:System.Windows.Forms.UserControl>には、コントロールに少なくとも1つのパブリックコンストラクターが必要です。

> [!NOTE]
> **UserControl Test Container**を使用して、Visual C++ のコントロールをテストすることはできません。

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>UserControl の実行時の動作をテストする

1. Visual Studio で、Windows コントロールライブラリプロジェクトを作成し、 **TestContainerExample**という名前を指定します。

2. **Windows フォームデザイナー**で、コントロールを<xref:System.Windows.Forms.Label> **ツールボックス** からコントロールのデザイン画面にドラッグします。

3. **F5**キーを押してプロジェクトをビルドし、 **UserControl テストコンテナー**を実行します。 <xref:System.Windows.Forms.UserControl> **プレビュー**ウィンドウに、テストコンテナーがと共に表示されます。

4. **プレビューウィンドウ**の右側にある<xref:System.Windows.Forms.PropertyGrid>コントロールに表示されるプロパティを選択します。<xref:System.Windows.Forms.Control.BackColor%2A> 値を**ControlDark**に変更します。 コントロールが濃い色に変化することを確認します。 他のプロパティ値を変更し、コントロールに対する影響を確認します。

5. **プレビュー**ウィンドウの下にある **[Dock Fill User Control]** チェックボックスをクリックします。 ウィンドウに合わせてコントロールのサイズが変更されていることを確認します。 テストコンテナーのサイズを変更し、ウィンドウのサイズが変更されたことを確認します。

6. テストコンテナーを閉じます。

7. **TestContainerExample**プロジェクトに別のユーザーコントロールを追加します。

8. **Windows フォームデザイナー**で、コントロールを<xref:System.Windows.Forms.Button> **ツールボックス** からコントロールのデザイン画面にドラッグします。

9. **F5**キーを押してプロジェクトをビルドし、テストコンテナーを実行します。

10. 2つのユーザーコントロールを切り替えるには、[**ユーザーの選択] コントロール**<xref:System.Windows.Forms.ComboBox>をクリックします。

## <a name="test-user-controls-from-another-project"></a>別のプロジェクトからユーザーコントロールをテストする

現在のプロジェクトのテストコンテナー内の他のプロジェクトからユーザーコントロールをテストできます。

1. Visual Studio で、Windows コントロールライブラリプロジェクトを作成し、 **TestContainerExample2**という名前を指定します。

2. **Windows フォームデザイナー**で、コントロールを<xref:System.Windows.Forms.RadioButton> **ツールボックス** からコントロールのデザイン画面にドラッグします。

3. **F5**キーを押してプロジェクトをビルドし、テストコンテナーを実行します。 <xref:System.Windows.Forms.UserControl> **プレビュー**ウィンドウに、テストコンテナーがと共に表示されます。

4. **[読み込み]** ボタンをクリックします。

5. **[開く]** ダイアログボックスで、前の手順で作成した**TestContainerExample**に移動します。 **TestContainerExample**を選択し、 **[開く]** ボタンをクリックしてユーザーコントロールを読み込みます。

6. **TestContainerExample**プロジェクトから2つのユーザーコントロールを切り替えるには、 **[ユーザーの選択] コントロール**<xref:System.Windows.Forms.ComboBox>を使用します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- [方法: 複合コントロールの作成](how-to-author-composite-controls.md)
- [チュートリアル: 複合コントロールの作成](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [ユーザーコントロールデザイナー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
