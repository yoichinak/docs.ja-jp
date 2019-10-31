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
ms.openlocfilehash: 5e05ec7fc503565333a4d05662a4e40d8d1193af
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197468"
---
# <a name="use-wpf-controls-in-windows-forms-apps"></a>Windows フォームアプリで WPF コントロールを使用する

Windows フォームベースのアプリケーションでは、Windows Presentation Foundation (WPF) コントロールを使用できます。 これらは2つの異なるビューテクノロジですが、円滑に相互運用されます。

Visual Studio の Windows フォームデザイナーには、Windows Presentation Foundation コントロールをホストするためのビジュアルデザイン環境が用意されています。 WPF コントロールは、<xref:System.Windows.Forms.Integration.ElementHost>という名前の特殊な Windows フォームコントロールによってホストされます。 このコントロールにより、WPF コントロールはフォームのレイアウトに参加し、キーボードおよびマウスメッセージを受け取ることができます。 デザイン時には、Windows フォームコントロールの場合と同じように <xref:System.Windows.Forms.Integration.ElementHost> コントロールを配置できます。

WPF ベースのアプリケーションでは、Windows フォームコントロールを使用することもできます。 詳細については、「 [Visual Studio での XAML のデザイン](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)」を参照してください。

## <a name="see-also"></a>関連項目

- [WPF と Windows フォームの相互運用](../../wpf/advanced/wpf-and-windows-forms-interoperation.md)
