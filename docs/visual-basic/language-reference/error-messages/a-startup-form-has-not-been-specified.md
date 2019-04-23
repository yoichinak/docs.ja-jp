---
title: スタートアップ フォームが指定されていません。
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
ms.openlocfilehash: 2bbae640ca65c95411cae24a9506fe2076b62cba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296473"
---
# <a name="a-startup-form-has-not-been-specified"></a>スタートアップ フォームが指定されていません。
アプリケーションを使用して、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>クラスが、スタートアップ フォームを指定しません。  
  
 これは、場合に発生することができます、**アプリケーション フレームワークを有効にする**プロジェクト デザイナー チェック ボックスが選択されているが、**スタートアップ フォーム**が指定されていません。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1. アプリケーションのスタートアップ オブジェクトを指定します。  
  
     詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
2. 上書き、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>を設定するメソッド、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>スタートアップ フォームのプロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>
- [Visual Basic アプリケーション モデルの概要](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
