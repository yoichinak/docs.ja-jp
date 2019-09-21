---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 80571933bc8d91c074dbee62aad50cece6277d51
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665511"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses メソッド

指定された functionId と rejitId は、現在存在する、このコードのすべての just-in-time バージョンのネイティブコードの開始アドレスを列挙します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

#### <a name="parameters"></a>パラメーター

`functionId` \
からネイティブコードの開始アドレスを返す関数の ID。

`reJitId` \
[in] JIT 再コンパイルされた関数のID。

`cCodeStartAddresses` \
[in] `codeStartAddresses` 配列の最大サイズ。

`pcCodeStartAddresses` \
入出力使用可能なアドレスの数。

`codeStartAddresses` \
入出力の`UINT_PTR`配列。各は、指定された関数のネイティブ本体の開始アドレスです。

## <a name="remarks"></a>Remarks

階層化コンパイルが有効になっている場合、関数は複数のネイティブコード本体を持つことができます。

## <a name="requirements"></a>必要条件

**・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。

**ヘッダー:** Corprof.idl、Corprof.idl

**ライブラリ**CorGuids .lib

**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)
