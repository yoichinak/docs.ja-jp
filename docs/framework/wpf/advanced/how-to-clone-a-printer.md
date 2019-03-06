---
title: '方法: プリンターを複製する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
ms.openlocfilehash: b3d05c3165e54735cfe739c3c0e227ec4b974c7b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378807"
---
# <a name="how-to-clone-a-printer"></a>方法: プリンターを複製する
ほとんどの企業が、ある時点で、購入、同じモデルの複数のプリンターです。 通常、これらがすべてインストールと実質的に同じ構成設定。 かかることがあります各プリンターをインストールしてエラーが発生します。 <xref:System.Printing.IndexedProperties?displayProperty=nameWithType>名前空間と<xref:System.Printing.PrintServer.InstallPrintQueue%2A>Microsoft .NET Framework で公開されているクラスでは、すぐに既存の印刷キューから任意の数の複製がその他の印刷キューをインストールすることです。  
  
## <a name="example"></a>例  
 次の例では、2 番目の印刷キューは既存の印刷キューから複製されました。 最初の 2 つ目とは異なる、名前、場所、ポート、および共有状態でのみです。 これを行うための主要な手順は次のとおりです。  
  
1.  作成、<xref:System.Printing.PrintQueue>クローンを作成することは、既存のプリンターのオブジェクト。  
  
2.  作成、<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>から、<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>の<xref:System.Printing.PrintQueue>します。 <xref:System.Collections.DictionaryEntry.Value%2A>このディクショナリ内の各エントリのプロパティから派生した型の 1 つのオブジェクトである<xref:System.Printing.IndexedProperties.PrintProperty>します。 このディクショナリ内のエントリの値を設定する 2 つの方法はあります。  
  
    -   使用して、辞書の**削除**と<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A>エントリを削除し、目的の値に再び追加する方法。  
  
    -   使用して、辞書の<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A>メソッド。  
  
     次の例では、両方の方法を示します。  
  
3.  作成、<xref:System.Printing.IndexedProperties.PrintBooleanProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 「とき」にし、その<xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A>に`true`。  
  
4.  使用して、<xref:System.Printing.IndexedProperties.PrintBooleanProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の「とき」のエントリ。  
  
5.  作成、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName"にし、その<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>に適切な<xref:System.String>。  
  
6.  使用して、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の"ShareName"エントリ。  
  
7.  別の作成<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 「場所」にし、その<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>に適切な<xref:System.String>。  
  
8.  もう 1 つを使用して、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の「場所」のエントリ。  
  
9. 配列を作成する<xref:System.String>秒。 各項目は、サーバー上のポートの名前です。  
  
10. 使用<xref:System.Printing.PrintServer.InstallPrintQueue%2A>を新しい値で、新しいプリンターをインストールします。  
  
 例を次にします。  
  
 [!code-csharp[ClonePrinter#ClonePrinter](~/samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Printing.IndexedProperties>
- <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>
- <xref:System.Printing.LocalPrintServer>
- <xref:System.Printing.PrintQueue>
- <xref:System.Collections.DictionaryEntry>
- [WPF のドキュメント](documents-in-wpf.md)
- [印刷の概要](printing-overview.md)
