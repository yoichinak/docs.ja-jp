---
title: WPF コントロールの使用
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5ea92b24a2ca30c0ad137d83c8f521a952ad0c6b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658501"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Windows フォームアプリで WPF コントロールを使用する

Windows フォームベースのアプリケーションでは、Windows Presentation Foundation (WPF) コントロールを使用できます。 これらは2つの異なるビューテクノロジですが、円滑に相互運用されます。

Visual Studio の Windows フォームデザイナーには、Windows Presentation Foundation コントロールをホストするためのビジュアルデザイン環境が用意されています。 WPF コントロールは、という名前<xref:System.Windows.Forms.Integration.ElementHost>の特殊な Windows フォームコントロールによってホストされます。 このコントロールにより、WPF コントロールはフォームのレイアウトに参加し、キーボードおよびマウスメッセージを受け取ることができます。 デザイン時には、Windows フォームコントロールと<xref:System.Windows.Forms.Integration.ElementHost>同じようにコントロールを配置できます。

WPF ベースのアプリケーションでは、Windows フォームコントロールを使用することもできます。 詳細については、「 [Visual Studio での XAML のデザイン](/visualstudio/designers/designing-xaml-in-visual-studio)」を参照してください。

## <a name="see-also"></a>関連項目

- [WPF と Windows フォームの相互運用](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)
