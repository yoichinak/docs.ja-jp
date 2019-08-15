---
title: 基本フォームの外観を変更した場合の影響
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms [Windows Forms]
- inherited forms [Windows Forms], modifications to base form
- Windows Forms, base form appearance
- base forms
- inheritance [Windows Forms], forms
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
ms.openlocfilehash: 5239017eb63ca6360ae8811a76497256fafbd1b1
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040143"
---
# <a name="effects-of-modifying-a-base-forms-appearance"></a>基本フォームの外観を変更した場合の影響

アプリケーションの開発中に、同じプロジェクト (または他のプロジェクト) 内の他のフォームの継承元となる、基本フォームの外観の変更が必要になることがよくあります。

デザイン時にプロパティの設定の変更やコントロールの追加または削除によって基本フォームの外観を変更した場合、基本フォームを含むプロジェクトをビルドしたときに、継承されたフォームに変更が反映されます。 基本フォームの変更を保存するだけでは、変更は反映されません。 プロジェクトをビルドするには、 **[ビルド]** メニューの **[ビルド]** を選択します。

実行時に基本フォームに変更を加えても、既にインスタンス化されている継承されたフォームには反映されません。

## <a name="see-also"></a>関連項目

- [base](~/docs/csharp/language-reference/keywords/base.md)
- [方法: Windows フォームを継承する](how-to-inherit-windows-forms.md)
- [Windows フォームのビジュアルの継承](windows-forms-visual-inheritance.md)
