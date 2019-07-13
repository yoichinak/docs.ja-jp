---
title: '方法: Windows フォーム アプリケーションでのフォント パターンの変更に応答する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 9fd7f99b35730cf867bfad5da24bc3f223e9a0f8
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425334"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>方法: Windows フォーム アプリケーションでのフォント パターンの変更に応答する
Windows オペレーティング システムでは、ユーザーが表示される既定のフォントのサイズを変更するシステム全体のフォント設定を変更できます。 これらのフォント設定を変更することは、視覚障害のある、各自の画面にテキストを読み取るより大きい型を必要とするユーザーにとって重要です。 フォントの設定を変更するたびに、フォームと含まれているすべてのテキストのサイズを増減してこれらの変更に対応するため、Windows フォーム アプリケーションを調整することができます。 フォント サイズの変更を動的に対応するために、フォームを設定する場合は、フォームにコードを追加できます。  
  
 通常、Windows フォームで使用される既定のフォントは、によって返されるフォント、<xref:Microsoft.Win32>名前空間の呼び出し`GetStockObject(DEFAULT_GUI_FONT)`します。 この呼び出しによって返されたフォントは、画面の解像度が変更されたときにのみ変更します。 コードの既定のフォントを変更する必要があります、次の手順に示すように<xref:System.Drawing.SystemFonts.IconTitleFont%2A>フォント サイズの変更に応答します。  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>デスクトップのフォントを使用して、フォント パターンの変更に応答するには  
  
1. フォームを作成し、目的のコントロールを追加します。 詳細については、「[方法 :コマンドラインから Windows フォーム アプリケーションを作成](how-to-create-a-windows-forms-application-from-the-command-line.md)と[Windows フォームで使用するコントロール](./controls/controls-to-use-on-windows-forms.md)します。  
  
2. 参照を追加、<xref:Microsoft.Win32>をコードに名前空間。  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. 必要なイベントのハンドラーをフックし、フォームの使用中の既定のフォントを変更するのには、フォームのコンス トラクターに次のコードを追加します。  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. ハンドラーを実装、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>イベントは、フォームを自動的にスケーリングするときに、<xref:Microsoft.Win32.UserPreferenceCategory.Window>カテゴリの変更。  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. 最後のハンドラーを実装、<xref:System.Windows.Forms.Form.FormClosing>デタッチ イベント、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>イベント ハンドラー。  
  
     > [!IMPORTANT]
     > このコードを含めないと、アプリケーションでメモリ リークが発生します。  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. コードをコンパイルして実行します。  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Windows XP では、フォントのスキームを手動で変更するには  
  
1. Windows デスクトップを右クリックして、Windows フォーム アプリケーションの実行中に**プロパティ**ショートカット メニューから。  
  
2. **表示プロパティ**ダイアログ ボックスで、をクリックして、**外観**タブ。  
  
3. **フォント サイズ**ドロップダウン リスト ボックスで、新しいフォントのサイズを選択します。  
  
     フォームがデスクトップ フォント パターンの実行時の変更に反応ようになりましたことがわかります。 間、ユーザーが変更されたとき**標準**、**大きいフォント**、および**特大フォント**フォームのフォントを変更し、スケールが適切です。  
  
## <a name="example"></a>例  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 このコード例では、コンス トラクターには呼び出しが含まれています`InitializeComponent`、これは Visual Studio で新しい Windows フォーム プロジェクトを作成するときに定義されています。 コマンドラインでアプリケーションを構築している場合は、次のコード行を削除します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Windows フォームにおける自動スケーリング](automatic-scaling-in-windows-forms.md)
