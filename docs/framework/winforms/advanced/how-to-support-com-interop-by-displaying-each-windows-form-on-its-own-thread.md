---
title: '方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用機能をサポートする'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306388"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>方法: 独自のスレッドで各 Windows フォームを表示して COM 相互運用をサポートする

.NET Framework メッセージループでフォームを表示することによって、COM 相互運用性の問題を解決できます。 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>これは、メソッドを使用して作成できます。

Windows フォームが COM クライアント アプリケーションから正しく動作するには、Windows フォームのメッセージ ループ上でフォームを実行する必要があります。 そのためには、次の方法のいずれかを使用します。

- <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> メソッドを使用して、Windows フォームを表示します。 詳細については、「[方法 :ShowDialog メソッド](com-interop-by-displaying-a-windows-form-shadow.md)を使用して Windows フォームを表示することにより、COM 相互運用をサポートします。

- 各 Windows フォームを別のスレッドで表示します。

この機能は Visual Studio で幅広くサポートされています。

[チュートリアル: 独自のスレッド](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))で各 Windows フォームを表示することにより、COM 相互運用をサポートします。

## <a name="example"></a>例

次のコード例は、個別のスレッドでフォームを表示し、 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> メソッドを呼び出して、スレッドで Windows フォーム メッセージ ポンプを開始する方法を示しています。 この方法を使用するには、 <xref:System.Windows.Forms.Control.Invoke%2A> メソッドを使用して、アンマネージ アプリケーションからのフォームの呼び出しをマーシャリングする必要があります。

この方法は、独自のメッセージ ループを使用して、独自のスレッドで、フォームの各インスタンスが実行する必要があります。 1 つのスレッドに対して複数のメッセージ ループを実行することはできません。 そのため、クライアント アプリケーションのメッセージ ループを変更することはできません。 ただし、.NET Framework コンポーネントを変更して、独自のメッセージループを使用する新しいスレッドを開始することもできます。

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a>コードのコンパイル

`COMForm`、 `Form1`、および `FormManager` の型を、 `COMWinform.dll`と呼ばれるアセンブリにコンパイルします。 「 [COM 向けアセンブリのパッケージ化](../../interop/packaging-an-assembly-for-com.md)」で説明するメソッドのいずれかを使用して COM にアセンブリを登録します。 これで、アンマネージ アプリケーションのアセンブリと対応する型のライブラリ (.tlb) ファイルを使用できます。 たとえば、Visual Basic 6.0 の実行可能なプロジェクトで参照として型ライブラリを使用することができます。

## <a name="see-also"></a>関連項目

- [COM への .NET Framework コンポーネントの公開](../../interop/exposing-dotnet-components-to-com.md)
- [COM 向けアセンブリのパッケージ化](../../interop/packaging-an-assembly-for-com.md)
- [COM へのアセンブリの登録](../../interop/registering-assemblies-with-com.md)
- [2 つのオブジェクトが等しいかどうかをテストする方法ShowDialog メソッドで Windows フォームを表示して COM 相互運用をサポートする](com-interop-by-displaying-a-windows-form-shadow.md)
- [Windows フォームおよびアンマネージ アプリケーションの概要](windows-forms-and-unmanaged-applications-overview.md)
