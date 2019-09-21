---
title: '#undef - C# リファレンス'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605590"
---
# <a name="undef-c-reference"></a>#undef (C# リファレンス)
`#undef` を使用すると、シンボルを未定義にすることができます。未定義のシンボルを [#if](./preprocessor-if.md) ディレクティブで式として使用すると、その式は `false` と評価されます。  
  
 シンボルは、[#define](./preprocessor-define.md) ディレクティブまたは [-define](../compiler-options/define-compiler-option.md) コンパイラ オプションのいずれかで定義できます。 `#undef` ディレクティブは、ファイル内で、ディレクティブではない他のステートメントよりも前に記述する必要があります。  
  
## <a name="example"></a>例  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

**DEBUG が定義されていません**

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
