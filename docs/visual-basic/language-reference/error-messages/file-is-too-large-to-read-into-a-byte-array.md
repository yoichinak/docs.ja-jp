---
title: バイト配列に読み取るにはファイルが大きすぎます。
ms.date: 07/20/2015
ms.assetid: 686630a6-a439-46c7-8d7b-34613ae4c5d8
ms.openlocfilehash: a842205e9184355e4ea750ea2eb32e4bcf05a14d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665104"
---
# <a name="file-is-too-large-to-read-into-a-byte-array"></a>バイト配列に読み取るにはファイルが大きすぎます。
バイト配列に読み取ろうとしているファイルのサイズが 4 GB を超えています。 `My.Computer.FileSystem.ReadAllBytes` メソッドは、このサイズを超えるファイルを読み取ることができません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- <xref:System.IO.StreamReader> を使用してファイルを読み取ります。 詳細については、「[.NET Framework のファイル I/O とファイル システムの基礎 (Visual Basic)](../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:System.IO.StreamReader>
- [Visual Basic におけるファイル アクセス](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
- [方法: StreamReader を使用してファイルからテキストを読み取る](../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-text-from-files-with-a-streamreader.md)
