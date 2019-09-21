---
title: '#else - C# リファレンス'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: d6a514f71b3526b2ffe347cdd971b81907fb0aad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605720"
---
# <a name="else-c-reference"></a>#else (C# リファレンス)
`#else` を使用すると、複合条件付きディレクティブを作成できるため、先行する [#if](./preprocessor-if.md) または (省略可能な) [#elif](./preprocessor-elif.md) ディレクティブの式がいずれも `true` に評価されない場合は、コンパイラが `#else` と以降の `#endif` の間のすべてのコードを評価します。  
  
## <a name="remarks"></a>解説  
 [#endif](./preprocessor-endif.md) が、`#else` の後の次のプリプロセッサ ディレクティブになる必要があります。 `#else` の使用例については、「[#if](./preprocessor-if.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# プリプロセッサ ディレクティブ](./index.md)
