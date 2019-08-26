---
title: '#warning - C# リファレンス'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608526"
---
# <a name="warning-c-reference"></a>#warning (C# リファレンス)
`#warning` を使用すると、コード内の特定の場所から [CS1030](../../misc/cs1030.md) レベル 1 のコンパイラの警告を生成できます。 例:  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a>解説
 `#warning` は条件付きディレクティブ内で一般的に使用されます。 [#error](./preprocessor-error.md) を使用してユーザー定義のエラーを生成することもできます。  
  
## <a name="example"></a>例  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
