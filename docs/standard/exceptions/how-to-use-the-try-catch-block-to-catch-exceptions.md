---
title: '方法: Try ブロックと Catch ブロックを使用して例外をキャッチする'
ms.date: 02/06/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- exceptions, try/catch blocks
- try blocks
- try/catch blocks
- catch blocks
ms.assetid: a3ce6dfd-1f64-471b-8ad8-8cfaf406275d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eaa389f461e70aae41f2e09437fd725a3bcefa5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696727"
---
# <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Try ブロックと Catch ブロックを使用して例外をキャッチする方法

例外を発生またはスローする可能性のあるコード ステートメントはいずれも `try` ブロックに配置し、1 つまたは複数の例外を処理するのに使用されるステートメントは `try` ブロックの下にある 1 つまたは複数の `catch` ブロックに配置します。 各 `catch` ブロックには例外の種類が含まれており、その例外の種類を処理するのに必要なステートメントを追加で含めることができます。

次の例では、<xref:System.IO.StreamReader> を使用して、*data.txt* と呼ばれるファイルを開き、そのファイルから行を取得します。 コードからは 3 つの例外のいずれかがスローされる可能性があります。そのため、コードは `try` ブロックに配置します。 3 つの `catch` ブロックでは例外がキャッチされます。さらに結果をコンソールに表示してそれらの例外が処理されます。

[!code-csharp[CatchException#3](~/samples/snippets/csharp/VS_Snippets_CLR/CatchException/CS/catchexception2.cs#3)]
[!code-vb[CatchException#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/CatchException/VB/catchexception2.vb#3)]

共通言語ランタイム (CLR) では、`catch` ブロックで処理されない例外がキャッチされます。 CLR によって例外がキャッチされると、ご利用の CLR 構成に応じて次の結果のいずれかが発生する場合があります。

- **[デバッグ]** ダイアログ ボックスが表示されます。
- プログラムの実行が停止され、例外情報を含むダイアログ ボックスが表示されます。
- [標準エラー出力ストリーム](xref:System.Console.Error)にエラーが出力されます。

> [!NOTE]
> ほとんどのコードで例外がスローされる可能性があります。また、<xref:System.OutOfMemoryException> のように、CLR 自体によっていつでもスローされる可能性のある例外もあります。 アプリケーションではこのようの例外を処理する必要はありませんが、他のユーザーが使用するライブラリを記述する際には、必要となる可能性があるので注意してください。 `try` ブロック内でコードを設定するタイミングに関しては、「[例外の推奨事項](best-practices-for-exceptions.md)」を参照してください。

## <a name="see-also"></a>関連項目

- [例外](index.md)
- [.NET での I/O エラーの処理](../io/handling-io-errors.md)
