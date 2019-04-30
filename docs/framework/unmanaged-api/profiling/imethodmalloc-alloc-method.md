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
ms.openlocfilehash: 9a676989bdc6866f85fabe3e15b1e6b7b8b5a9a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000715"
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