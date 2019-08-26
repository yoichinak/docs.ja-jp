---
title: メソッドのパラメーター - C# リファレンス
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 4011cbd3bc9306b64df87b1fcde48f1f41df8240
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602044"
---
# <a name="method-parameters-c-reference"></a>メソッドのパラメーター (C# リファレンス)

[in](./in-parameter-modifier.md)、[ref](./ref.md) または [out](./out-parameter-modifier.md) のないメソッドで宣言されたパラメーターは、呼び出されたメソッドに値で渡されます。 メソッドでその値を変更できますが、呼び出し元のプロシージャに制御が渡されるときに、変更された値は保持されません。 メソッド パラメーターのキーワードを使用して、この動作を変更できます。  
  
 ここでは、メソッドのパラメーターを宣言するときに使用できるキーワードについて説明します。  
  
- [params](./params.md) は、このパラメーターが異なる数の引数を取得する可能性があることを指定します。
  
- [in](./in-parameter-modifier.md) は、このパラメーターが参照によって渡されますが、呼び出されたメソッドでは読み取りのみが行われることを指定します。
  
- [ref](./ref.md) は、このパラメーターが参照によって渡され、呼び出されたメソッドでは読み取りまたは書き込みが行われる可能性があることを指定します。
  
- [out](./out-parameter-modifier.md) は、このパラメーターが参照によって渡され、呼び出されたメソッドでは書き込みが行われることを指定します。
  
## <a name="see-also"></a>関連項目

- [C# リファレンス](../index.md)
- [C# プログラミング ガイド](../../programming-guide/index.md)
- [C# のキーワード](./index.md)
