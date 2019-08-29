---
title: Visual Studio での式ツリーのデバッグ (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 3334828475ef5d933ea660ea33ae264d4ccce172
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106877"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio での式ツリーのデバッグ (Visual Basic)
アプリケーションをデバッグするときに、式ツリーの構造および内容を分析できます。 式ツリーの構造の概要を簡単に取得するには、`DebugView` プロパティ使用できます。このプロパティでは、[特殊な構文を使って](debugview-syntax.md)式ツリーが表されます。 (`DebugView` はデバッグ モードでのみ使用できることに注意してください。)  

![Visual Studio デバッガー内での式ツリーの DebugView](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

`DebugView` は文字列なので、[組み込まれているテキスト ビジュアライザー](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)を使って、複数行で表示できます。**テキスト ビジュアライザー**を使うには、`DebugView` ラベルの隣にある虫眼鏡アイコンから選択します。

 !["DebugView" の結果に適用されたテキスト ビジュアライザー](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

または、式ツリー用の[カスタム ビジュアライザー](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)をインストールして使うこともできます。例:

- [ReadableExpressions](https://github.com/agileobjects/ReadableExpressions) ([MIT ライセンス](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)、[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers) で使用可能): 式ツリーが C# コードとしてレンダリングされます。

  ![ReadableExpressions ビジュアライザー](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

- [式ツリービジュアライザー](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees)([MIT ライセンス](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) は、式ツリー、そのプロパティ、および関連オブジェクトのグラフィカルビューを提供します。とは Visual Basic コードを使用して式ツリーを表示できます。

  ![ExpressionToString ビジュアライザー](media/debugging-expression-trees-in-visual-studio/expression_to_string_visualizer_vb.png)

### <a name="to-open-a-visualizer-for-an-expression-tree"></a>式ツリーのビジュアライザーを開くには  
  
1. **[データヒント]** 、 **[ウォッチ]** ウィンドウ、 **[自動変数]** ウィンドウ、または **[ローカル]** ウィンドウで、式ツリーの横に表示されている虫眼鏡のアイコンをクリックします。  
  
     使用可能なビジュアライザーの一覧が表示されます。 

      ![Visual Studio からビジュアライザーを開く](media/debugging-expression-trees-in-visual-studio/expression_tree_visualizers_vb.png)

2. 使用するビジュアライザーをクリックします。  

## <a name="see-also"></a>関連項目

- [式ツリー (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)
- [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)
- [カスタム ビジュアライザーを作成する](/visualstudio/debugger/create-custom-visualizers-of-data)
- [`DebugView` 構文](debugview-syntax.md)
