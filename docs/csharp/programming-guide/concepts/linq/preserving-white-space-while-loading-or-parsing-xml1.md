---
title: XML の読み込み時または解析時の空白の維持1
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: 68b52f1d69c57b4292f02fea932e392de4a3ffc8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64596799"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>XML の読み込み時または解析時の空白の維持
このトピックでは、空白に対する [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の動作を制御する方法について説明します。  
  
 一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。  
  
 もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。  
  
 このトピックでは、空白に対する、XML ツリーを設定するメソッドの動作について説明します。 XML ツリーをシリアル化するときの空白の制御については、「[シリアル化時の空白の維持](../../../../csharp/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)」を参照してください。  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ツリーを設定するメソッドの動作  
 <xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーを設定します。 XML ツリーは、ファイル、<xref:System.IO.TextReader>、<xref:System.Xml.XmlReader>、または文字列から設定することができます。  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 メソッドが <xref:System.Xml.Linq.LoadOptions> を引数として受け取らない場合、意味のない空白は維持されません。  
  
 ほとんどの場合、メソッドが <xref:System.Xml.Linq.LoadOptions> を引数として受け取ると、意味のない空白を XML ツリー内のテキスト ノードとして維持できます。これは、オプションの動作です。 ただし、メソッドが <xref:System.Xml.XmlReader> から XML を読み込んでいる場合は、<xref:System.Xml.XmlReader> によって空白を維持するかどうかが決定されます。 <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> を設定しても効果はありません。  
  
 これらのメソッドで空白を維持すると、意味のない空白が <xref:System.Xml.Linq.XText> ノードとして XML ツリーに挿入されます。 空白が維持されない場合、テキスト ノードは挿入されません。  
  
 <xref:System.Xml.XmlWriter> を使用して、XML ツリーを作成することができます。 <xref:System.Xml.XmlWriter> に書き込まれたノードが、ツリーに挿入されます。 ただし、このメソッドを使用して XML ツリーを構築すると、ノードが空白かどうかにかかわらず、また空白に意味があるかどうかにかかわらず、すべてのノードが維持されます。  
  
## <a name="see-also"></a>関連項目

- [XML の解析 (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
