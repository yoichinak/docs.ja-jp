---
title: Visual Studio (Visual Basic) で式ツリーのデバッグ
ms.date: 07/20/2015
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
ms.openlocfilehash: 9aead09e0e9469f13e2d6befbad444d3c7fecabd
ms.sourcegitcommit: 96543603ae29bc05cecccb8667974d058af63b4a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/24/2019
ms.locfileid: "66196024"
---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Visual Studio (Visual Basic) で式ツリーのデバッグ
アプリケーションをデバッグするときに、式ツリーの構造および内容を分析できます。 式ツリーの構造体の簡単な概要を取得するには、使用することができます、`DebugView`プロパティは、式ツリーを表す[特別な構文を使用して](debugview-syntax.md)します。 (`DebugView` はデバッグ モードでのみ使用できることに注意してください。)  

![Visual Studio デバッガー内での式ツリーの DebugView](media/debugging-expression-trees-in-visual-studio/debugview_vb.png)

`DebugView` は文字列なので、[組み込まれているテキスト ビジュアライザー](https://docs.microsoft.com/visualstudio/debugger/view-strings-visualizer#open-a-string-visualizer)を使って、複数行で表示できます。**テキスト ビジュアライザー**を使うには、`DebugView` ラベルの隣にある虫眼鏡アイコンから選択します。

 !["DebugView" の結果に適用されたテキスト ビジュアライザー](media/debugging-expression-trees-in-visual-studio/string_visualizer_vb.png)

インストールして使用する代わりに、[カスタム ビジュアライザー](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)式ツリーなど。

* [ReadableExpressions](https://github.com/agileobjects/ReadableExpressions) ([MIT ライセンス](https://github.com/agileobjects/ReadableExpressions/blob/master/LICENSE.md)、[Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=vs-publisher-1232914.ReadableExpressionsVisualizers) で使用可能): 式ツリーが C# コードとしてレンダリングされます。

  ![ReadableExpressions ビジュアライザー](media/debugging-expression-trees-in-visual-studio/readable_expressions_visualizer.png)

* [式ツリーのビジュアライザー](https://github.com/zspitz/ExpressionToString#visual-studio-debugger-visualizer-for-expression-trees) ([MIT ライセンス](https://github.com/zspitz/ExpressionToString/blob/master/LICENSE)) を式ツリー、そのプロパティ、および関連するオブジェクトのグラフィカル ビューを提供し、Visual Basic コードを使用して式ツリーを表示することができます。

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
