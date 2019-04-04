---
title: '方法: データ入力用のサイズ変更可能な Windows フォームを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 57c6d30b63b15f5e57e813c1deb90d3da5a5ba35
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705715"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>方法: データ入力用のサイズ変更可能な Windows フォームを作成します。
レイアウトが優れていると、その親フォームの寸法の変更に柔軟に対応できます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用すると、フォームの寸法の変更に応じて一貫した方法でコントロールの位置とサイズが変更されるように、フォームのレイアウトを調整できます。 <xref:System.Windows.Forms.TableLayoutPanel> コントロールは、コントロールの内容の変更によってレイアウトの変更が生じる場合にも便利です。 この手順で説明するプロセスは、Visual Studio 環境内で実行できます。  参照してください[チュートリアル。データ エントリのサイズ変更可能な Windows フォームを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))します。  
  
## <a name="example"></a>例  
 ユーザーによるフォームのサイズ変更に適切に対応するレイアウトを <xref:System.Windows.Forms.TableLayoutPanel> コントロールを使用して作成する方法を次の例に示します。 また、ローカリゼーションに適切に対応するレイアウトも示します。  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Data、System.Drawing、および System.Windows.Forms の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [方法: 固定およびドッキング TableLayoutPanel コントロールで子コントロール](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [方法: ローカリゼーションに対応する Windows フォーム レイアウトをデザインします。](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Microsoft Windows ユーザー エクスペリエンス、Official Guidelines for ユーザー インターフェイス開発者および設計者です。Redmond、WA:Microsoft Press、1999 年。(USBN:0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
