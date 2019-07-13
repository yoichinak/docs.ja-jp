---
title: '方法: クリップボードにデータを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 06ce64de5e2a6b4aa299b9ad9c41982b7c1924c7
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348278"
---
# <a name="how-to-add-data-to-the-clipboard"></a>方法: クリップボードにデータを追加する
<xref:System.Windows.Forms.Clipboard>クラスは、Windows オペレーティング システムのクリップボード機能との対話に使用できるメソッドを提供します。 多くのアプリケーションは、クリップボードをデータの一時的なリポジトリとして使用されます。 たとえば、ワード プロセッサでは、切り取りと貼り付けの操作中に、クリップボードを使用します。 クリップボードも別に 1 つのアプリケーションからデータを転送するために役立ちます。  
  
 クリップボードにデータを追加すると、その形式を使用する場合、その他のアプリケーションは、データを認識できるように、データ形式を指定できます。 データを使用できる可能性のあるその他のアプリケーションの数を増やすに複数の異なる形式でクリップボードにデータを追加することもできます。  
  
 クリップボードの形式は、その形式を使用するアプリケーションに関連付けられているデータを取得できるようにする形式を識別する文字列です。 <xref:System.Windows.Forms.DataFormats>クラスは、使用する定義済みの形式名を提供します。 独自の形式名を使用してもまたはその形式として、オブジェクトの型を使用できます。  
  
 1 つまたは複数の形式でクリップボードにデータを追加するには、使用、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>メソッド。 この方法では、任意のオブジェクトを渡すことができますが、複数の形式でデータを追加する必要があります最初に、データを追加する別のオブジェクトが複数の形式を扱うために設計されています。 データを追加する、通常、<xref:System.Windows.Forms.DataObject>を実装する任意の型を使用することができますが、<xref:System.Windows.Forms.IDataObject>インターフェイス。  
  
 .NET Framework 2.0 では、クリップボードの基本的な作業を容易に設計された新しいメソッドを使用して、クリップボードに直接データを追加できます。 テキストなどの 1 つの一般的な形式でデータを操作する場合は、これらのメソッドを使用します。  
  
> [!NOTE]
>  すべての Windows ベースのアプリケーションでは、クリップボードを共有します。 そのため、別のアプリケーションに切り替えた場合に、内容は変更される可能性が。  
>   
>  <xref:System.Windows.Forms.Clipboard>クラスは、シングル スレッド アパートメント (STA) モードに設定するスレッドでのみ使用できます。 このクラスを使用することを確認、`Main`メソッドが設定されて、<xref:System.STAThreadAttribute>属性。  
>   
>  オブジェクトはクリップボードに配置するためにシリアル化可能である必要があります。 型をシリアル化可能にするには、マークで、<xref:System.SerializableAttribute>属性。 クリップボードのメソッドにシリアル化できないオブジェクトを渡すと、例外をスローせず、メソッドは失敗します。 シリアル化の詳細については、「<xref:System.Runtime.Serialization>」を参照してください。  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>1 つの一般的な形式でクリップボードにデータを追加するには  
  
1. 使用して、 <xref:System.Windows.Forms.Clipboard.SetAudio%2A>、 <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、 <xref:System.Windows.Forms.Clipboard.SetImage%2A>、または<xref:System.Windows.Forms.Clipboard.SetText%2A>メソッド。 これらのメソッドは、.NET Framework 2.0 でのみ使用できます。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>カスタム形式でクリップボードにデータを追加するには  
  
1. 使用して、<xref:System.Windows.Forms.Clipboard.SetData%2A>メソッドをカスタム形式名を使用します。 このメソッドは、.NET Framework 2.0 でのみ使用できます。  
  
     定義済みの形式名を使用することも、<xref:System.Windows.Forms.Clipboard.SetData%2A>メソッド。 詳細については、「 <xref:System.Windows.Forms.DataFormats> 」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>複数の形式でクリップボードにデータを追加するには  
  
1. 使用して、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A?displayProperty=nameWithType>メソッドを渡します、<xref:System.Windows.Forms.DataObject>データを格納しています。 このメソッドを使用して、.NET Framework 2.0 より前のバージョンをクリップボードにデータを追加する必要があります。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>関連項目

- [ドラッグ アンド ドロップ操作とクリップボードのサポート](drag-and-drop-operations-and-clipboard-support.md)
- [方法: クリップボードからデータを取得します。](how-to-retrieve-data-from-the-clipboard.md)
