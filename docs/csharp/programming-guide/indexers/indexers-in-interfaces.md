---
title: インターフェイスのインデクサー - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: cea8d157e89597ddf4633cf7f7d3df7044db9ec7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589447"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>インターフェイスのインデクサー (C# プログラミング ガイド)
[interface](../../language-reference/keywords/interface.md) でインデクサーを宣言することができます。 インターフェイスのインデクサーのアクセサーは、[クラス](../../language-reference/keywords/class.md)のインデクサーのアクセサーと次の点で異なります。  
  
- インターフェイスのアクセサーは、修飾子は使用しません。  
  
- インターフェイスのアクセサーには、本文はありません。  
  
 したがって、アクセサーの目的は、インデクサーが読み取り/書き込み、読み取り専用、または書き込み専用のどれかを示すことです。  
  
 インターフェイスのインデクサー アクセサーの例を次に示します。  
  
 [!code-csharp[csProgGuideIndexers#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#3)]  
  
 インデクサーのシグネチャは、同じインターフェイスで宣言されている他のすべてのインデクサーの署名とは異なる必要があります。  
  
## <a name="example"></a>例  
 次の例では、インターフェイスのインデクサーを実装する方法について説明します。  
  
 [!code-csharp[csProgGuideIndexers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#4)]  
  
 前の例では、インターフェイス メンバーの完全修飾名を使用して明示的なインターフェイス メンバーの実装を使用することができます。 例:  
  
```  
string ISomeInterface.this[int index]   
{   
}   
```  
  
 ただし、完全修飾名は、クラスが同じインデクサーの署名を持つ 2 つ以上のインターフェイスを実装するときにあいまいさを避けるためにのみ必要です。 たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスが同じインデクサーの署名を持っている場合、明示的なインターフェイス メンバーの実装が必要です。 つまり、次のインデクサーの宣言があります。  
  
```  
string IEmployee.this[int index]   
{   
}   
```  
  
 これは、`IEmployee` インターフェイス上でインデクサーを実装します。次の宣言があります。  
  
```  
string ICitizen.this[int index]
{   
}   
```  
  
 これは、`ICitizen` インターフェイスでインデクサーを実装します。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [インデクサー](./index.md)
- [プロパティ](../classes-and-structs/properties.md)
- "[インターフェイス](../interfaces/index.md)"
