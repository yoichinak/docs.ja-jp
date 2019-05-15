---
title: IMethodMalloc::Alloc メソッド
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66bd56a332dc34fd35f3129256cc0e3d6c5d4508
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636697"
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc メソッド

新しい Microsoft intermediate language (MSIL) 関数本体の指定された量のメモリを割り当てようとします。

## <a name="syntax"></a>構文

```cpp
PVOID Alloc (
    [in] ULONG   cb
);
```

## <a name="parameters"></a>パラメーター

`cb`\
[in]メソッド本体を割り当てバイト数。

## <a name="remarks"></a>Remarks

 割り当てられたメモリは、このアロケーターに関連付けられているモジュールのベース アドレスよりも大きいアドレスに開始されます。 つまり、各アロケーターは、特定のモジュールが作成され、そのベース アドレスから正のオフセットにメモリを割り当てることを試みます。 場合`Alloc`要求されたモジュールのベース アドレスよりも大きいアドレスにあるバイト数を割り当てに失敗する実際の使用可能なメモリ領域の量に関係なく、E_OUTOFMEMORY が返されます。

 `Alloc`メソッドを組み合わせて使用する必要があります、 [icorprofilerinfo::setilfunctionbody](icorprofilerinfo-setilfunctionbody-method.md)メソッド。

## <a name="requirements"></a>必要条件
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** CorProf.idl、CorProf.h

 **ライブラリ:** CorGuids.lib

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [IMethodMalloc インターフェイス](imethodmalloc-interface.md)
