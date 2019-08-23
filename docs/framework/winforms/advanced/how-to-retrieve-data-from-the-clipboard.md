---
title: '方法: クリップボードからデータを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: 88c2f2d872ae32b2cb3f0df13ce4816400695385
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963782"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>方法: クリップボードからデータを取得する
クラス<xref:System.Windows.Forms.Clipboard>には、Windows オペレーティングシステムのクリップボード機能との対話に使用できるメソッドが用意されています。 多くのアプリケーションでは、データの一時リポジトリとしてクリップボードを使用します。 たとえば、ワードプロセッサは、切り取りと貼り付けの操作中にクリップボードを使用します。 クリップボードは、アプリケーション間で情報を転送する場合にも役立ちます。  
  
 アプリケーションによっては、データを複数の形式でクリップボードに格納することで、データを使用する可能性のある他のアプリケーションの数を増やすことができます。 クリップボード形式は、形式を識別する文字列です。 識別された形式を使用するアプリケーションは、クリップボードにある関連データを取得できます。 クラス<xref:System.Windows.Forms.DataFormats>には、使用するための定義済みの形式名が用意されています。 独自の形式名を使用することも、形式としてオブジェクトの型を使用することもできます。 クリップボードにデータを追加する方法につい[ては、「」を参照してください。クリップボード](how-to-add-data-to-the-clipboard.md)にデータを追加します。  
  
 クリップボードに特定の形式のデータが含まれているかどうか`Contains`を確認するに<xref:System.Windows.Forms.Clipboard.GetData%2A>は、いずれかの*書式*メソッドまたはメソッドを使用します。 クリップボードからデータを取得するには、いずれ`Get`かの*書式*メソッド<xref:System.Windows.Forms.Clipboard.GetData%2A>またはメソッドを使用します。 これらのメソッドは .NET Framework 2.0 で新しく追加されたものです。  
  
 .NET Framework 2.0 より前のバージョンを使用してクリップボードのデータにアクセス<xref:System.Windows.Forms.Clipboard.GetDataObject%2A?displayProperty=nameWithType>するには、メソッドを使用し<xref:System.Windows.Forms.IDataObject>て、返されるのメソッドを呼び出します。 たとえば、返されたオブジェクトで特定の形式が使用可能かどうかを判断<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>するには、メソッドを呼び出します。  
  
> [!NOTE]
> すべての Windows ベースのアプリケーションは、システムクリップボードを共有します。 そのため、別のアプリケーションに切り替えると、コンテンツが変更される可能性があります。  
>   
>  クラス<xref:System.Windows.Forms.Clipboard>は、シングルスレッドアパートメント (STA) モードに設定されているスレッドでのみ使用できます。 このクラスを使用するには、 `Main`メソッドが<xref:System.STAThreadAttribute>属性でマークされていることを確認します。  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>1つの共通形式でクリップボードからデータを取得するには  
  
1. 、、、または<xref:System.Windows.Forms.Clipboard.GetText%2A>メソッドを使用します。 <xref:System.Windows.Forms.Clipboard.GetImage%2A> <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A> <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A> 必要に応じて、 `Contains`対応する*書式*メソッドを使用して、データを特定の形式で使用できるかどうかを判断します。 これらのメソッドは、.NET Framework 2.0 でのみ使用できます。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>カスタム形式でクリップボードからデータを取得するには  
  
1. カスタム書式<xref:System.Windows.Forms.Clipboard.GetData%2A>名を使用して、メソッドを使用します。 このメソッドは、.NET Framework 2.0 でのみ使用できます。  
  
     メソッドでは、 <xref:System.Windows.Forms.Clipboard.SetData%2A>定義済みの書式名を使用することもできます。 詳細については、「 <xref:System.Windows.Forms.DataFormats> 」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>複数の形式でクリップボードからデータを取得するには  
  
1. <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> メソッドを使用します。 .NET Framework 2.0 より前のバージョンのクリップボードからデータを取得するには、このメソッドを使用する必要があります。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>関連項目

- [ドラッグ アンド ドロップ操作とクリップボードのサポート](drag-and-drop-operations-and-clipboard-support.md)
- [方法: クリップボードにデータを追加する](how-to-add-data-to-the-clipboard.md)
