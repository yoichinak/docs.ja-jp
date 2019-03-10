---
title: Windows フォーム デザイナーでのデザイン時エラー
ms.date: 03/30/2017
f1_keywords:
- DTELErrorList
- WhyDTELPage
helpviewer_keywords:
- errors [Windows Forms Designer]
- design-time errors [Windows Forms Designer]
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
ms.openlocfilehash: 64a0b8d0d0d9f0cc2bc2a841b999af58f29b4f75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718052"
---
# <a name="design-time-errors-in-the-windows-forms-designer"></a>Windows フォーム デザイナーでのデザイン時エラー
このトピックでは、Windows フォーム デザイナーで読み込みに失敗したときに場合に Microsoft Visual Studio に表示されるデザイン時のエラー リストの意味と使用法について説明します。 このエラー リストが表示された場合、デザイナーのバグであると解釈するのではなく、コード内のエラーを修正するための参考情報であると考えてください。  
  
 エラーに関する詳細情報と考えられる解決策が提示されるので、このエラー リストの基本を理解することによって、アプリケーションのデバッグに役立てることができます。  
  
## <a name="the-design-time-error-list-interface"></a>デザイン時のエラー リスト インターフェイス  
 Windows フォーム デザイナーで読み込めない場合、デザイナーにエラー リストが表示されます。 エラーは複数のカテゴリに分類されています。 たとえば、宣言されていない変数の 4 つのインスタンスがある場合、それらは同じエラー カテゴリに分類されます。 各エラー カテゴリには、エラーの概要を示す簡単な説明が含まれます。  
  
 エラー カテゴリの見出しをクリックするか、展開/折りたたみシェブロンをクリックすることで、エラー カテゴリを展開したり、折りたたんだりできます。 エラー カテゴリを展開すると、次の追加のヘルプが表示されます。  
  
-   このエラーのインスタンス。  
  
-   このエラーのヘルプ。  
  
-   このエラーに関するフォーラムの投稿。  
  
### <a name="instances-of-this-error"></a>このエラーのインスタンス  
 追加のヘルプには、現在のプロジェクトにおけるエラーのすべてのインスタンスが一覧表示されます。 多くのエラーには、次の形式の正確な場所が含まれます: *[プロジェクト名]* *[フォーム名]* 行:*[行番号]* 列:*[列番号]*。 **[コードに移動]** リンクを使用して、エラーが発生したコード内の場所に移動できます。  
  
 呼び出し履歴がエラーに関連付けられている場合、**[コール スタックの表示]** リンクをクリックすると、エラーがさらに展開され、呼び出し履歴が表示されます。 履歴を調べると、有用なデバッグ情報を得られる可能性があります。 たとえば、エラーが発生する前に呼び出された関数を追跡できます。 呼び出し履歴を選択して、コピーおよび保存できます。  
  
> [!NOTE]
>  Visual Basic では、デザイン時エラー リストには複数のエラーは表示されませんが、同じエラーの複数のインスタンスが表示される場合があります。 Visual C++ では、エラーに goto コード リンク/行番号リンクはありません。  
  
### <a name="help-with-this-error"></a>このエラーのヘルプ  
 エラーには、関連する MSDN ヘルプ トピックへのリンクが含まれており、追加のヘルプにはヘルプ トピックへのリンクが含まれています。 リンクをクリックすると、関連するヘルプ トピックが Visual Studio に表示されます。  
  
### <a name="forum-posts-about-this-error"></a>このエラーに関するフォーラムの投稿  
 追加のヘルプには、エラーに関連する MSDN フォーラムの投稿へのリンクが含まれています。 フォーラムは、エラー メッセージの文字列に基づいて検索されます。 次のフォーラムを検索することもできます。  
  
-   [Windows フォーム デザイナーのフォーラム](https://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows フォームのフォーラム](https://go.microsoft.com/fwlink/?LinkId=203523)  
  
### <a name="ignore-and-continue"></a>無視して続行する  
 エラー状態を無視して、デザイナーの読み込みを続行することもできます。 この操作を選択すると、予期しない動作が発生する可能性があります。 たとえば、デザイン サーフェイスにコントロールが表示されない場合があります。  
  
## <a name="see-also"></a>関連項目
- [デザイン時開発のトラブルシューティング](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171843(v=vs.120))
- [コントロールとコンポーネントの作成時のトラブルシューティング](troubleshooting-control-and-component-authoring.md)
- [デザイン時の Windows フォーム コントロールの開発](developing-windows-forms-controls-at-design-time.md)
- [Windows フォーム デザイナーのエラー メッセージ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233640(v=vs.100))
