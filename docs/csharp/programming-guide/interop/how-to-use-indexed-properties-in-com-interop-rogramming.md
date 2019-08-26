---
title: '方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する - C# プログラミング ガイド'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- indexed properties [C#]
- Office programming [C#], indexed properties
- properties [C#], indexed
ms.assetid: 756bfc1e-7c28-4d4d-b114-ac9288c73882
ms.openlocfilehash: c39b9a313d265187605d51a2c78c7d3d3dcdb056
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923912"
---
# <a name="how-to-use-indexed-properties-in-com-interop-programming-c-programming-guide"></a>方法: COM 相互運用機能を使用したプログラミングでインデックス付きプロパティを使用する (C# プログラミング ガイド)
"*インデックス付きプロパティ*" により、パラメーターを持つ COM プロパティが C# プログラミングでいっそう使いやすくなります。 インデックス付きプロパティは、[名前付き引数と省略可能な引数](../classes-and-structs/named-and-optional-arguments.md)、新しい型 ([dynamic](../../language-reference/keywords/dynamic.md))、[埋め込み型情報](../concepts/assemblies-gac/walkthrough-embedding-types-from-managed-assemblies-in-visual-studio.md)などの Visual C# の他の機能と連携して、Microsoft Office プログラミングをいっそう強力なものにします。  
  
 以前のバージョンの C# では、プロパティとしてメソッドにアクセスできるのは、`get` メソッドがパラメーターを持たず、`set` メソッドが 1 つだけ値パラメーターを持つ場合に限られました。 しかし、すべての COM プロパティがこのような制限を満たしているわけではありません。 たとえば、Excel の <xref:Microsoft.Office.Interop.Excel.Range.Range%2A> プロパティには、範囲の名前のパラメーターを必要とする `get` アクセサーがあります。 これまでは、このような `Range` プロパティに直接アクセスすることはできず、次の例に示すように、`get_Range` メソッドを代わりに使う必要がありました。  
  
 [!code-csharp[csProgGuideIndexedProperties#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#1)]  
  
 インデックス付きプロパティを使うと、次のようなコードを記述できます。  
  
 [!code-csharp[csProgGuideIndexedProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#2)]  
  
> [!NOTE]
> また、前の例では、[省略可能な引数](../classes-and-structs/named-and-optional-arguments.md)機能も使われており、`Type.Missing` を省略できます。  
  
 C# 3.0 以前で <xref:Microsoft.Office.Interop.Excel.Range> オブジェクトの `Value` プロパティの値を設定する場合と同様に、2 つの引数が必要です。 1 つのパラメーターでは、範囲の値の型を指定する省略可能なパラメーターの引数を渡します。 そしてもう 1 つのパラメーターで、`Value` プロパティの値を渡します。 次の例は、これらの方法を示したものです。 どちらも、セル A1 の値を `Name` に設定しています。
  
 [!code-csharp[csProgGuideIndexedProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#3)]  
  
 インデックス付きプロパティを使うと、次のようなコードを記述できます。  
  
 [!code-csharp[csProgGuideIndexedProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#4)]  
  
 独自のインデックス付きプロパティを作成することはできません。 この機能では、既存のインデックス付きプロパティの使用のみがサポートされます。  
  
## <a name="example"></a>例  
 次に完全なコードの例を示します。 Office API にアクセスするプロジェクトを設定する方法について詳しくは、「[方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](./how-to-access-office-onterop-objects.md)」をご覧ください。  
  
 [!code-csharp[csProgGuideIndexedProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguideindexedproperties/cs/program.cs#5)]  
  
## <a name="see-also"></a>関連項目

- [名前付き引数と省略可能な引数](../classes-and-structs/named-and-optional-arguments.md)
- [dynamic](../../language-reference/keywords/dynamic.md)
- [dynamic 型の使用](../types/using-type-dynamic.md)
- [方法: Office プログラミングで名前付き引数と省略可能な引数を使用する](../classes-and-structs/how-to-use-named-and-optional-arguments-in-office-programming.md)
- [方法: Visual C# の機能を使用して Office 相互運用オブジェクトにアクセスする](./how-to-access-office-onterop-objects.md)
- [チュートリアル:Office プログラミング](./walkthrough-office-programming.md)
