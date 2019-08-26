---
title: '方法: テキスト ファイルから読み込む - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- StreamReader.ReadToEnd
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
ms.openlocfilehash: 2b98f24da7f13ae752f248eb8f26c75c1d47a824
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923950"
---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>方法: テキスト ファイルから読み込む (C# プログラミング ガイド)
この例では、<xref:System.IO.File?displayProperty=nameWithType> クラスの静的メソッド <xref:System.IO.File.ReadAllText%2A> と <xref:System.IO.File.ReadAllLines%2A> を使用してテキスト ファイルの内容を読み取ります。  
  
 <xref:System.IO.StreamReader> の使用例については、「[方法: テキスト ファイルを一度に 1 行読み込む](./how-to-read-a-text-file-one-line-at-a-time.md)」をご覧ください。  
  
> [!NOTE]
> この例で使用されるファイルは、「[方法: テキスト ファイルに書き込む](./how-to-write-to-a-text-file.md)」のトピックで作成されます。  
  
## <a name="example"></a>例  
 [!code-csharp[csFilesandFolders#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#4)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 コードをコピーし、C# のコンソール アプリケーションに貼り付けます。  
  
 「[方法: テキスト ファイルに書き込む](./how-to-write-to-a-text-file.md)」のテキスト ファイルを使わない場合は、`ReadAllText` と `ReadAllLines` の引数を、ご使用のコンピューター上適切なパスおよびファイル名に置き換えます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
- ファイルが存在しない、または指定した場所に存在しない。 ファイル名のパスとスペルを確認してください。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名に基づいてファイルの内容を判断しないでください。 たとえば、`myFile.cs` というファイルが C# のソース ファイルではない可能性もあります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.IO?displayProperty=nameWithType>
- [C# プログラミング ガイド](../index.md)
- [ファイル システムとレジストリ (C# プログラミング ガイド)](./index.md)
