---
title: インターフェイスのプロパティ - C# プログラミング ガイド
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: cdd425970442e284d6fd6488bbb13394c12e939a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596454"
---
# <a name="interface-properties-c-programming-guide"></a>インターフェイスのプロパティ (C# プログラミング ガイド)
[interface](../../language-reference/keywords/interface.md) でプロパティを宣言することができます。 インターフェイスのプロパティ アクセサーの例を次に示します。  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 インターフェイス プロパティのアクセサーには、本文はありません。 したがって、アクセサーの目的は、プロパティが読み取り/書き込み、読み取り専用、または書き込み専用のどれかを示すことです。  
  
## <a name="example"></a>例  
 この例では、インターフェイス `IEmployee` に読み取り/書き込み専用のプロパティ `Name` および読み取り専用のプロパティ `Counter` があります。 クラス `Employee` は `IEmployee` インターフェイスを実装し、これら 2 つのプロパティを使用します。 プログラムは、新しい従業員の名前と現在の従業員の数を読み込んで、従業員の名前と計算した従業員番号を表示します。  
  
 メンバーが宣言されているインターフェイスを参照するプロパティの完全修飾名を使用することができます。 次に例を示します。  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 これは、[明示的なインターフェイスの実装](../interfaces/explicit-interface-implementation.md)で呼び出されます。 たとえば、`Employee` クラスが 2 つのインターフェイス `ICitizen` と `IEmployee` を実装し、両方のインターフェイスが同じ `Name` プロパティを持っている場合、明示的なインターフェイス メンバーの実装が必要です。 つまり、次のプロパティの宣言があります。  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 これは、`IEmployee` インターフェイスで `Name` プロパティを実装します。次の宣言があります。  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 これは、`ICitizen` インターフェイスで `Name` プロパティを実装します。  
  
 [!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a>出力例  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../index.md)
- [プロパティ](./properties.md)
- [プロパティの使用](./using-properties.md)
- [プロパティとインデクサーの比較](../indexers/comparison-between-properties-and-indexers.md)
- [インデクサー](../indexers/index.md)
- [インターフェイス](../interfaces/index.md)
