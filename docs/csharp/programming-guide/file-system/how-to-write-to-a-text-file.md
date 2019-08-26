---
title: '方法: テキスト ファイルに書き込む - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
ms.openlocfilehash: d08fe23f2dbfe46c0a58084b05610dfe7db3dda9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589921"
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>方法: テキスト ファイルに書き込む (C# プログラミング ガイド)
テキストをファイルに書き込むさまざまな方法を次の例に示します。 最初の 2 つの例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの便利な静的メソッドを使用して、すべての `IEnumerable<string>` の各要素と文字列をテキスト ファイルに記述しています。 例 3 は、ファイルに書き込むときに各行を個別に処理する必要がある場合にテキストをファイルに追加する方法を示します。 例 1 ～ 3 ではすべての既存の内容が上書きされます。例 4 に、既存のファイルにテキストを追加する方法を示します。  
  
 これらの例はいずれもリテラル文字列をファイルに書き込みます。 ファイルに書き込まれるテキストの書式を設定する場合は、<xref:System.String.Format%2A> メソッドまたは C# の[文字列補間](../../language-reference/tokens/interpolated.md)機能を使用します。  
  
## <a name="example"></a>例  
 [!code-csharp[csFilesandFolders#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#3)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
- ファイルは存在するが、読み取り専用である。  
  
- パス名が長すぎる。  
  
- ディスクがいっぱいになっている。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [ファイル システムとレジストリ (C# プログラミング ガイド)](./index.md)
- [サンプル: コレクションをアプリケーション ストレージに保存する](https://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
