---
title: '方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
ms.openlocfilehash: 81220ad4c0bf00a38abfe7257d5fc61e92e8d885
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206448"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする
[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メッセージ ループで Windows フォームを表示して、コンポーネント オブジェクト モデル (COM) 相互運用性の問題を解決できます。これは、 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> メソッドを使用して作成されます。  
  
 フォームが COM クライアント アプリケーションから正しく動作するには、Windows フォームのメッセージ ループ上で実行する必要があります。 そのためには、次の方法のいずれかを使用します。  
  
-   <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して、Windows フォームを表示します。  
  
-   各 Windows フォームを別のスレッドで表示します。 詳細については、「[方法 :独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポート](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)します。  
  
## <a name="procedure"></a>プロシージャ  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メッセージ ループにフォームを表示する方法としては、すべての方法の中で実装する必要があるコードが最も少ない [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メソッドを使用する方法が最も簡単です。  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドは、管理されていないアプリケーションのメッセージ ループを一時停止し、フォームをダイアログ ボックスとして表示します。 ホスト アプリケーションのメッセージ ループが一時停止されているので、 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドは、新しい [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メッセージ ループを作成してフォームのメッセージを処理します。  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用する場合の欠点は、フォームがモーダル ダイアログ ボックスとして開かれることです。 この動作により、Windows フォームが開かれている間は呼び出し元のアプリケーションですべてのユーザー インターフェイス (UI) がブロックされます。 ユーザーがフォームを終了すると、 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メッセージ ループが終了し、以前のアプリケーションのメッセージ ループの実行が再び開始されます。  
  
 フォームを表示するためのメソッドが含まれるクラス ライブラリを Windows フォームで作成し、その後で COM 相互運用機能のクラス ライブラリをビルドすることができます。 Visual Basic 6.0 または Microsoft Foundation Classes (MFC) からこの DLL ファイルを使用し、これらのいずれかの環境から <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを呼び出してフォームを表示することができます。  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする方法  
  
-   <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> コンポーネントで、 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドのすべての呼び出しを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] メソッドの呼び出しに置き換えます。  
  
## <a name="see-also"></a>関連項目

- [COM への .NET Framework コンポーネントの公開](../../interop/exposing-dotnet-components-to-com.md)
- [方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートします。](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
- [Windows Forms and Unmanaged Applications](windows-forms-and-unmanaged-applications.md)
