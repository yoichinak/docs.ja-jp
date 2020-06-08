---
title: '方法 : URL からプロトコルとポート番号を抽出する'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, examples
- parsing text with regular expressions, examples
- regular expressions, examples
- .NET Framework regular expressions, examples
- regular expressions [.NET Framework], examples
- pattern-matching with regular expressions, examples
ms.assetid: ab7f62b3-6d2c-4efb-8ac6-28600df5fd5c
ms.openlocfilehash: 48f2bf5c0d9af0a3fc286561ba978f86d1f11ac8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290488"
---
# <a name="how-to-extract-a-protocol-and-port-number-from-a-url"></a>方法 : URL からプロトコルとポート番号を抽出する
次の例では、URL からプロトコルとポート番号を抽出します。  
  
## <a name="example"></a>例  
 例では <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドを使用して、後にコロンとポート番号が続くプロトコルを返します。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/Example.cs#1)]
 [!code-vb[RegularExpressions.Examples.Protocol#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/Example.vb#1)]  
  
 この正規表現パターン `^(?<proto>\w+)://[^/]+?(?<port>:\d+)?/` の解釈を次の表に示します。  
  
|パターン|[説明]|  
|-------------|-----------------|  
|`^`|文字列の先頭から照合を開始します。|  
|`(?<proto>\w+)`|1 つ以上の単語文字に一致します。 このグループに `proto` と名前を付けます。|  
|`://`|後に 2 つのスラッシュ記号が続くコロンと一致します。|  
|`[^/]+?`|スラッシュ記号以外の任意の文字の 1 回以上の (ただし、可能な限り少ない) 出現と一致します。|  
|`(?<port>:\d+)?`|後に 1 桁以上の文字が続くコロンの 0 回または 1 回の出現と一致します。 このグループに `port` と名前を付けます。|  
|`/`|スラッシュ記号に一致します。|  
  
 <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドは、正規表現パターンでキャプチャされた 2 つの名前付きグループの値を連結する、`${proto}${port}` 置換シーケンスを展開します。 これは、<xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> プロパティによって返されたコレクション オブジェクトから取得した文字列を明示的に連結するための便利な代替です。  
  
 例では、<xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> メソッドを 2 つの置換 `${proto}` と `${port}` とともに使用して、キャプチャされたグループを出力文字列に含めます。 代わりに、次のコードに示されているように、一致の <xref:System.Text.RegularExpressions.GroupCollection> オブジェクトから、キャプチャされたグループを取得することができます。  
  
 [!code-csharp[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/cs/example2.cs#2)]
 [!code-vb[RegularExpressions.Examples.Protocol#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Examples.Protocol/vb/example2.vb#2)]  
  
## <a name="see-also"></a>参照

- [.NET の正規表現](regular-expressions.md)
