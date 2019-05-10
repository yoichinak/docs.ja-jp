---
title: アンセーフ コードとポインター - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: 9f4e74e1e8fa71d1492a10162191822c1edfb635
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64608036"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a>アンセーフ コードとポインター (C# プログラミング ガイド)
タイプ セーフとセキュリティを維持するために、既定では C# はポインター演算をサポートしません。 ただし、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使用すれば、ポインターを使用できる unsafe コンテキストを定義できます。 ポインターの詳細については、「[ポインター型 (C# プログラミング ガイド)](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)」を参照してください。  
  
> [!NOTE]
>  共通言語ランタイム (CLR) では、アンセーフ コードは検査できないコードと呼ばれます。 C# のアンセーフ コードは、必ずしも危険ではありません。ただ、CLR で安全性を検査できないコードであるというだけです。 そのため CLR は、完全に信頼できるアセンブリ内にある場合にのみ、アンセーフ コードを実行します。 アンセーフ コードを使用する場合は、セキュリティ上のリスクやポインター エラーが発生しないように注意してください。  
  
## <a name="unsafe-code-overview"></a>アンセーフ コードの概要  
 アンセーフ コードには次の特徴があります。  
  
- メソッド、型、およびコード ブロックをアンセーフとして定義できます。  
  
- アンセーフ コードでアプリケーションのパフォーマンスが向上することがあります。これは、配列のバインド チェックが削除されるためです。  
  
- アンセーフ コードは、ポインターを必要とするネイティブ関数を呼び出すときに必要です。  
  
- アンセーフ コードを使用すると、セキュリティと安定性の面でリスクが生じます。  
  
- C# でアンセーフ コードをコンパイルするには、[/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) を指定してアプリケーションをコンパイルする必要があります。  
  
## <a name="related-sections"></a>関連項目  
 詳細については次を参照してください:  
  
- [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
- [固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
- [方法: ポインターを使用してバイトの配列をコピーする](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
- [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)
