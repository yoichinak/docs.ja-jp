---
title: 'ICorProfilerInfo8:: GetDynamicFunctionInfo'
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 45a40d49cea2dd5f881fbd47cc2fb4bd96e8f9ff
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70243983"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8:: GetDynamicFunctionInfo メソッド

動的メソッドに関する情報を取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

#### <a name="parameters"></a>パラメーター

`functionId` \
から情報を取得する対象の関数の ID。

`moduleId` \
から関数の親クラスが定義されているモジュールへのポインター。

`ppvSig` \
入出力関数の署名へのポインター。

`pbSig` \
入出力関数シグネチャのバイト数へのポインター。

`cchName` \
[in] `wszName` 配列の最大サイズ。

`pcchName` \
入出力`wszName`配列内の文字数。

`wszName` \
入出力関数の名前`WCHAR` (存在する場合) の配列。

## <a name="remarks"></a>Remarks

IL スタブや LCG などの特定のメソッドには、 [IMetaDataImport](../metadata/imetadataimport-interface.md) Api と[IMetaDataImport2](../metadata/imetadataimport2-interface.md) api を使用して取得できるメタデータが関連付けられていません。 このようなメソッドは、命令ポインターを通じて、または[ICorProfilerCallback8::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)をリッスンすることによって、プロファイラーによって検出されます。

この API を使用して、表示名などの動的メソッドに関する情報を取得できます (使用可能な場合)。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** Corprof.idl、Corprof.idl

**ライブラリ**CorGuids .lib

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo8 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)
