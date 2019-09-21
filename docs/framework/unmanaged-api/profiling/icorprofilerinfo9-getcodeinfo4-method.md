---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: e6708971909c1035e41786f4d8dad1cf9afdffaf
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665613"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9:: GetCodeInfo4 メソッド

ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。

## <a name="syntax"></a>構文

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

#### <a name="parameters"></a>パラメーター

`pNativeCodeStartAddress` \
からネイティブ関数の先頭へのポインター。

`cCodeInfos` \
[in] `codeInfos` 配列のサイズ。

`pcCodeInfos` \
入出力使用できる[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体の合計数へのポインター。

`codeInfos` \
[out] 呼び出し元が提供したバッファー。 メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。

## <a name="remarks"></a>Remarks

`GetCodeInfo4` メソッドは、メソッドのさまざまなネイティブバージョンのコード情報を検索できる点を除いて、[GetCodeInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) に似ています。

> [!NOTE]
> `GetCodeInfo4`ガベージコレクションをトリガーできます。

エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。

が`GetCodeInfo4`返された後、 `codeInfos`バッファーがすべての[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体を格納するのに十分な大きさであったことを確認する必要があります。 これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) 構造体のサイズで除算された `cCodeInfos` が `pcCodeInfos` より小さい場合は、大きい `codeInfos` バッファーを割り当て、`cCodeInfos` を新しい大きいサイズに更新して、`GetCodeInfo4` を再度呼び出します。

別の方法として、最初に `GetCodeInfo4` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。 次に`codeInfos` 、バッファーサイズを`pcCodeInfos`で返される値に設定し、 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体のサイズを乗算して、 `GetCodeInfo4`を再度呼び出します。

## <a name="requirements"></a>必要条件

**・** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)」を参照してください。

**ヘッダー:** Corprof.idl、Corprof.idl

**ライブラリ**CorGuids .lib

**.Net のバージョン:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo9 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)
