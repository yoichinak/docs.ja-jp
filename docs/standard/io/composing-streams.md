---
title: ストリームの作成
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 452071e9726a95b4b3d9bb9cefe720d39bbc3e0c
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674348"
---
# <a name="compose-streams"></a>ストリームの作成
*バッキング ストア*は、ディスクやメモリなどの記憶域メディアです。 さまざまなバッキング ストアが <xref:System.IO.Stream> クラスの実装としてそれぞれ独自のストリームを実装しています。 

各ストリームの種類は、指定されたバッキング ストアとの間でバイトの読み取りと書き込みを行います。 バッキング ストアに接続するストリームは、*基本ストリーム*と呼ばれます。 基本ストリームにはコンストラクターがあり、ストリームをバッキング ストアに接続するために必要なパラメーターがそれに指定されます。 たとえば、<xref:System.IO.FileStream> には、プロセスでファイルを共有する方法を指定する path パラメーターを指定するコンストラクターがあります。  

<xref:System.IO> クラスは、簡易なストリーム構成で設計されています。 必要な機能を提供する 1 つ以上のパススルー ストリームに基本ストリームをアタッチできます。 好みの種類の読み取りまたは書き込みを簡単に実行できるように、チェーンの末端に閲覧者またはライターをアタッチできます。  

次のコード例では、*MyFile.txt* をバッファーするために既存の *MyFile.txt* を中心にして **FileStream** を作成します。 **FileStreams** は既定でバッファーされます。

>[!IMPORTANT]
>サンプルでは、*MyFile.txt* という名前のファイルがアプリと同じフォルダーに入っていると想定しています。  

## <a name="example-use-streamreader"></a>例:StreamReader を使用する
次の例では、**FileStream** から文字を読み取る <xref:System.IO.StreamReader> が作成されます。これはコンストラクター引数として **StreamReader** に渡されます。 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> は、<xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> によって文字が検出されなくなるまで読み取りを行います。  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>例:BinaryReader を使用する
次の例では、**FileStream** からバイト数を読み取る <xref:System.IO.BinaryReader> が作成されます。これはコンストラクター引数として **BinaryReader** に渡されます。 <xref:System.IO.BinaryReader.ReadByte%2A> は、<xref:System.IO.BinaryReader.PeekChar%2A> によってバイトが検出されなくなるまで読み取りを行います。  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
