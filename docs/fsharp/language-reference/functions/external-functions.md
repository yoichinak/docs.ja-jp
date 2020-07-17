---
title: 外部関数
description: ネイティブ コードで関数を呼び出すための F# 言語サポートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968729"
---
# <a name="external-functions"></a>外部関数

このトピックでは、ネイティブ コードで関数を呼び出すための F# 言語サポートについて説明します。

## <a name="syntax"></a>構文

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Remarks

前の構文では、*引数*は`System.Runtime.InteropServices.DllImportAttribute`属性に渡される引数を表します。 1つ目の引数は、この関数を含む DLL の名前を表す文字列です。 dll の拡張子はありません。 呼び出し規約など、 `System.Runtime.InteropServices.DllImportAttribute`クラスのパブリックプロパティに対して追加の引数を指定できます。

次のエクスポート関数をC++含むネイティブ DLL があるとします。

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

次のコードを使用して F# からこの関数を呼び出すことができます。

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

ネイティブコードとの相互運用性は*プラットフォーム呼び出し*と呼ばれ、CLR の機能です。 詳細については、「[アンマネージ コードとの相互運用](../../../framework/interop/index.md)」を参照してください。 そのセクションの情報は、F# に適用されます。

## <a name="see-also"></a>関連項目

- [関数](index.md)
