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
ms.openlocfilehash: f2fb48e07243694b14904b240bdcb0739175c2fc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593534"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>方法: ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする
使用して作成された .NET Framework のメッセージ ループ上の Windows フォームを表示して、コンポーネント オブジェクト モデル (COM) 相互運用性の問題を解決することができます、<xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>メソッド。  
  
 フォームが COM クライアント アプリケーションから正しく動作するには、Windows フォームのメッセージ ループ上で実行する必要があります。 そのためには、次の方法のいずれかを使用します。  
  
- <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して、Windows フォームを表示します。  
  
- 各 Windows フォームを別のスレッドで表示します。 詳細については、「[方法 :独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポート](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)します。  
  
## <a name="procedure"></a>プロシージャ  
 使用して、<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>メソッドはできるため、.NET Framework のメッセージ ループでフォームを表示する最も簡単な方法は、すべての方法の最小限のコードを実装する必要があります。  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドは、管理されていないアプリケーションのメッセージ ループを一時停止し、フォームをダイアログ ボックスとして表示します。 ホスト アプリケーションのメッセージ ループが中断されているため、<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>メソッドは、フォームのメッセージを処理する新しい .NET Framework メッセージ ループを作成します。  
  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用する場合の欠点は、フォームがモーダル ダイアログ ボックスとして開かれることです。 この動作により、Windows フォームが開かれている間は呼び出し元のアプリケーションですべてのユーザー インターフェイス (UI) がブロックされます。 ユーザーは、フォームを終了すると、.NET Framework のメッセージ ループが閉じし、アプリケーションの以前のメッセージ ループの実行が再開します。  
  
 フォームを表示するためのメソッドが含まれるクラス ライブラリを Windows フォームで作成し、その後で COM 相互運用機能のクラス ライブラリをビルドすることができます。 Visual Basic 6.0 または Microsoft Foundation Classes (MFC) からこの DLL ファイルを使用し、これらのいずれかの環境から <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを呼び出してフォームを表示することができます。  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>ShowDialog メソッドで Windows フォームを表示して COM 相互運用機能をサポートする方法  
  
- すべての呼び出しを置き換える、<xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType>メソッドの呼び出しを<xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>.NET Framework コンポーネントのメソッド。  
  
## <a name="see-also"></a>関連項目

- [COM への .NET Framework コンポーネントの公開](../../interop/exposing-dotnet-components-to-com.md)
- [方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートします。](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
- [Windows フォームとアンマネージ アプリケーション](windows-forms-and-unmanaged-applications.md)
