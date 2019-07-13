---
title: ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetFunctionFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs
helpviewer_keywords:
- ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
- GetFunctionFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: ce8f6aa6-4ebf-4a86-b429-4bbc8af41a8f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 31fad9e82d0b93360f92676f6357c136ae60634a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771127"
---
# <a name="icorprofilerinfo2getfunctionfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetFunctionFromTokenAndTypeArgs メソッド
取得、`FunctionID`クラスを格納している、指定したメタデータ トークンを使用して関数のおよび`ClassID`のいずれかの値が引数を入力します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFunctionFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdMethodDef funcDef,  
    [in] ClassID classId,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] FunctionID* pFunctionID);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleID`  
 [in]関数が存在するモジュールの ID。  
  
 `funcDef`  
 [in]`mdMethodDef`関数を参照するメタデータ トークン。  
  
 `classId`  
 [in]関数の外側のクラスの ID。  
  
 `cTypeArgs`  
 [in]指定された関数の型パラメーターの数。 この値は、非ジェネリック関数に 0 である必要があります。  
  
 `typeArgs`  
 [in]配列の`ClassID`関数の引数は、それぞれの値。 値`typeArgs`場合に NULL が`cTypeArgs`0 に設定されます。  
  
 `pFunctionID`  
 [out]ポインター、`FunctionID`指定された関数。  
  
## <a name="remarks"></a>Remarks  
 呼び出す、`GetFunctionFromTokenAndTypeArgs`メソッドを`mdMethodRef`メタデータの代わりに、`mdMethodDef`メタデータ トークンが予期しない結果を持つことができます。 呼び出し元を解決する必要があります、`mdMethodRef`を`mdMethodDef`渡すとき。  
  
 関数が既に読み込まれていない場合は、呼び出す`GetFunctionFromTokenAndTypeArgs`これはさまざまなコンテキストで危険な操作が発生する読み込みが発生します。 たとえば、モジュールまたは型の読み込み中にこのメソッドを呼び出すと、ランタイムが循環的に読み込みしよう無限ループが発生する可能性があります。  
  
 一般の使用`GetFunctionFromTokenAndTypeArgs`をお勧めします。 プロファイラー イベントを特定の関数の場合、保存する必要があります、`ModuleID`と`mdMethodDef`その関数、および使用の[icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)を確認するかどうかを指定した`FunctionID`は必要な関数です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
