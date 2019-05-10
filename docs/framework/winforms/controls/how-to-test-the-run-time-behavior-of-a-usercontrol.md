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
ms.openlocfilehash: 48531ab1ef3b30b6516e3f2e7b5858a8884cbfe8
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211704"
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a>方法: UserControl の実行時の動作をテストします。

開発する際に、<xref:System.Windows.Forms.UserControl>実行時の動作をテストする必要があります。 別の Windows ベースのアプリケーション プロジェクトを作成し、テスト フォーム上にコントロールを配置することができますが、この手順は便利です。 速くて簡単方法は使用する、 **UserControl Test Container** Visual Studio で提供します。 このテスト コンテナーは、Windows コントロール ライブラリ プロジェクトから直接開始します。

> [!IMPORTANT]
> テスト コンテナーを読み込む、<xref:System.Windows.Forms.UserControl>コントロールには、少なくとも 1 つのパブリック コンス トラクターが必要です。

> [!NOTE]
> **UserControl Test Container**を使用して、Visual C++ のコントロールをテストすることはできません。

## <a name="test-the-run-time-behavior-of-a-usercontrol"></a>UserControl の実行時の動作をテストします。

1. Visual Studio と呼ばれる Windows コントロール ライブラリ プロジェクトを作成**ファイルを開く**します。 詳細については、次を参照してください。 [Windows コントロール ライブラリ テンプレート](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))します。

2. **Windows フォーム デザイナー**、ドラッグ、<xref:System.Windows.Forms.Label>コントロールから、**ツールボックス**コントロールのデザイン サーフェイスにします。

3. キーを押して**F5**プロジェクトをビルドして実行する、 **UserControl Test Container**します。 テスト コンテナーが表示されます、<xref:System.Windows.Forms.UserControl>で、**プレビュー**ウィンドウ。

4. 選択、<xref:System.Windows.Forms.Control.BackColor%2A>に表示されるプロパティ、<xref:System.Windows.Forms.PropertyGrid>コントロールの右側に、**プレビュー**ウィンドウ。 その値を変更`ControlDark`します。 コントロールが暗い色に変わることを確認します。 その他のプロパティ値を変更してみてくださいをコントロールへの影響を確認します。

5. をクリックして、**ユーザー入力コントロールのドッキング**下のチェック ボックス、**プレビュー**ウィンドウ。 コントロールのサイズのウィンドウに入力することを確認します。 テスト コンテナーのサイズを変更し、ペイン コントロールのサイズをことを確認します。

6. テスト コンテナーを閉じます。

7. 別のユーザー コントロールを追加、**ファイルを開く**プロジェクト。 詳細については、「[方法: 既存の項目をプロジェクトに追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))します。

8. **Windows フォーム デザイナー**、ドラッグ、<xref:System.Windows.Forms.Button>コントロールから、**ツールボックス**コントロールのデザイン サーフェイスにします。

9. F5 キーを押してプロジェクトをビルドし、テスト コンテナーを実行します。

10. をクリックして、**ユーザー コントロールの選択**<xref:System.Windows.Forms.ComboBox>を 2 つのユーザー コントロールを切り替えます。

## <a name="test-user-controls-from-another-project"></a>別のプロジェクトからのテスト ユーザーのコントロール

現在のプロジェクトのテスト コンテナーでは、他のプロジェクトからユーザー コントロールをテストできます。

1. 呼ばれる Windows コントロール ライブラリ プロジェクトを作成**TestContainerExample2**します。 詳細については、次を参照してください。 [Windows コントロール ライブラリ テンプレート](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100))します。

2. **Windows フォーム デザイナー**、ドラッグ、<xref:System.Windows.Forms.RadioButton>コントロールから、**ツールボックス**コントロールのデザイン サーフェイスにします。

3. F5 キーを押してプロジェクトをビルドし、テスト コンテナーを実行します。 テスト コンテナーが表示されます、<xref:System.Windows.Forms.UserControl>で、**プレビュー**ウィンドウ。

4. をクリックして、**ロード**ボタンをクリックします。

5. **オープン** ダイアログ ボックスに移動**ファイルを開く**.dll で、前の手順で作成しました。 選択**ファイルを開く**.dll をクリックして、**オープン** ボタンをユーザー コントロールを読み込む

6. 使用して、**ユーザー コントロールの選択**<xref:System.Windows.Forms.ComboBox>から 2 つのユーザー コントロール間を切り替える、**ファイルを開く**プロジェクト。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.UserControl>
- [方法: 複合コントロールを作成](how-to-author-composite-controls.md)
- [チュートリアル: Visual Basic による複合コントロールの作成](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [チュートリアル: ビジュアルを含む複合コントロールの作成C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
- [ユーザー コントロール デザイナー](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/183c3hth(v=vs.100))
