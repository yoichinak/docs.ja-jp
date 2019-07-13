---
title: '方法: 文字列が数値を表しているかどうかを確認する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 626fce590ba08bbdabf27ac33287a0b46b592f9c
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423618"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>方法: 文字列が数値を表しているかどうかを確認する (C# プログラミング ガイド)
文字列が指定された数値型の有効な表現であるかどうかを確認するには、静的 `TryParse` メソッドを使用します。このメソッドには、すべてのプリミティブ数値型が実装されており、また <xref:System.DateTime>、<xref:System.Net.IPAddress> などの型も実装されています。 次の例では、"108" が有効な [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) かどうかを確認する方法を示します。  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 文字列が数値以外の文字、または指定した型で表すには大きすぎる (または小さすぎる) 数値の場合、`TryParse` は false を返し、out パラメーターを 0 に設定します。 それ以外の場合は true を返し、out パラメーターを文字列の数値に設定します。  
  
> [!NOTE]
>  文字列が数値文字列だけを含んでいても、使用する `TryParse` メソッドの型として有効ではない場合があります。 たとえば、"256" は `byte` の有効値ではありませんが、`int` としては有効です。 " 98.6" は `int` の有効値ではありませんが、有効な `decimal` です。  
  
## <a name="example"></a>例  
 次の例では、`long` 値、`byte` 値、および `decimal` 値の文字列表現を指定して `TryParse` を使用する方法を示します。  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 プリミティブ数値型は、`Parse` 静的メソッドも実装します。このメソッドは、文字列が有効な数値でない場合は例外をスローします。 一般に、数値が有効でない場合は単に false を返す `TryParse` の方が効率的です。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 テキスト ボックス、コンボ ボックスなどのコントロールからのユーザー入力を検証するには、常に `TryParse` メソッドまたは `Parse` メソッドを使用してください。  
  
## <a name="see-also"></a>関連項目

- [方法: バイト配列を int に変換する](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [方法: 文字列を数値に変換する](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [方法: 16 進文字列と数値型の間で変換する](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [数値文字列の解析](../../../standard/base-types/parsing-numeric.md)
- [型の書式設定](../../../standard/base-types/formatting-types.md)
