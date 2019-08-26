---
title: '#error - C# リファレンス'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: f18dbd007e80397b815256231a1d56e5ca50010e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608564"
---
# <a name="error-c-reference"></a>#error (C# リファレンス)
`#error` を使用すると、コード内の特定の場所からユーザー定義の [CS1029](../compiler-messages/cs1029.md) エラーを生成できます。 例:  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a>解説  
 `#error` は条件付きディレクティブ内で一般的に使用されます。  
  
 [#warning](./preprocessor-warning.md) を使用してユーザー定義の警告を生成することもできます。  
  
## <a name="example"></a>例  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
