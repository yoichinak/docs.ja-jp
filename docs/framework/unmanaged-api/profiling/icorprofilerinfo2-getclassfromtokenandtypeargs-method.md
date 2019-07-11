---
title: ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassFromTokenAndTypeArgs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs
helpviewer_keywords:
- GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassFromTokenAndTypeArgs method [.NET Framework profiling]
ms.assetid: b25c88f0-71b9-443b-8eea-1c94db0a44b9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a88a6c19a5c8b45576dd6f632adf70f7ec2eed55
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751877"
---
# <a name="icorprofilerinfo2getclassfromtokenandtypeargs-method"></a>ICorProfilerInfo2::GetClassFromTokenAndTypeArgs メソッド
取得、`ClassID`指定したメタデータ トークンを使用して型の`ClassID`いずれかの値が引数を入力します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetClassFromTokenAndTypeArgs(  
    [in] ModuleID moduleID,  
    [in] mdTypeDef typeDef,  
    [in] ULONG32 cTypeArgs,  
    [in, size_is(cTypeArgs)] ClassID typeArgs[],  
    [out] ClassID* pClassID);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleID`  
 [in]型が存在するモジュールの ID。  
  
 `typeDef`  
 [in]`mdTypeDef`型を参照するメタデータ トークン。  
  
 `cTypeArgs`  
 [in]指定した型の型パラメーターの数。 この値は、非ジェネリック型に対しては 0 である必要があります。  
  
 `typeArgs`  
 [in]配列の`ClassID`型の引数は、それぞれの値。 値`typeArgs`場合に NULL が`cTypeArgs`0 に設定されます。  
  
 `pClassID`  
 [out]ポインター、`ClassID`の指定した型。  
  
## <a name="remarks"></a>Remarks  
 呼び出す、`GetClassFromTokenAndTypeArgs`メソッドを`mdTypeRef`の代わりに、`mdTypeDef`メタデータ トークンが予期しない結果を持つことができます。 呼び出し元を解決する必要があります、`mdTypeRef`を、`mdTypeDef`渡すとき。  
  
 型が既に読み込まれていない場合は、呼び出す`GetClassFromTokenAndTypeArgs`読み込み、これはさまざまなコンテキストで危険な操作がトリガーされます。 たとえば、モジュールまたはその他の型の読み込み中にこのメソッドを呼び出すと、ランタイムが循環的に読み込みしよう無限ループが発生する可能性があります。  
  
 一般の使用`GetClassFromTokenAndTypeArgs`をお勧めします。 プロファイラー イベントは、特定の型の場合、保存する必要があります、`ModuleID`と`mdTypeDef`その種類、および使用の[icorprofilerinfo 2::getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)を確認するかどうかを指定した`ClassID`の目的の型。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
