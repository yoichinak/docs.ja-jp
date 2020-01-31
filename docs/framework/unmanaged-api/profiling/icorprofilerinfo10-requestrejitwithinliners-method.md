---
title: ICorProfilerInfo10::RequestReJITWithInliners
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.RequestReJITWithInliners
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 5822136eb1a7f582bcfae901a99775950e586198
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863180"
---
# <a name="icorprofilerinfo10requestrejitwithinliners-method"></a>ICorProfilerInfo10:: RequestReJITWithInliners メソッド

要求されたメソッドのほか、要求されたメソッドの inliners を再適用します。

## <a name="syntax"></a>構文

```cpp
HRESULT RequestReJITWithInliners( [in]                       DWORD       dwRejitFlags,
                                  [in]                       ULONG       cFunctions,
                                  [in, size_is(cFunctions)]  ModuleID    moduleIds[],
                                  [in, size_is(cFunctions)]  mdMethodDef methodIds[]);
```

## <a name="parameters"></a>パラメーター

- `dwRejitFlags`

  \[] [COR_PRF_REJIT_FLAGS](cor-prf-rejit-flags-enumeration.md)のビットマスク。

- `cFunctions`

  \[] 再コンパイルする関数の数。

- `moduleIds`

  \[in] 再コンパイルする関数を識別する (`module`、`methodDef`) のペアの `moduleId` の部分を指定します。

- `methodIds`

  \[in] 再コンパイルする関数を識別する (`module`、`methodDef`) のペアの `methodId` の部分を指定します。

## <a name="remarks"></a>コメント

[RequestReJIT](icorprofilerinfo4-requestrejit-method.md)では、インラインメソッドの追跡は行われません。 プロファイラーは、インライン化されたメソッドのすべてのインスタンスが ReJITted であることを確認するために、インライン展開をブロックするか、インライン展開を追跡し、すべての inliners に対して `RequestReJIT` を呼び出す必要がありました。 これにより、再インライン化を監視するためのプロファイラーが存在しないため、ReJIT on attach に問題が生じます。 このメソッドを呼び出すことにより、inliners の完全なセットも ReJITted になることを保証できます。

## <a name="requirements"></a>要件

**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)」を参照してください。

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 インターフェイス](icorprofilerinfo10-interface.md)
