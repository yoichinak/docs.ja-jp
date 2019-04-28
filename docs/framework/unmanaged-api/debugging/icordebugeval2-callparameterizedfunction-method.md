---
title: ICorDebugEval2::CallParameterizedFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CallParameterizedFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CallParameterizedFunction
helpviewer_keywords:
- ICorDebugEval2::CallParameterizedFunction method [.NET Framework debugging]
- CallParameterizedFunction method [.NET Framework debugging]
ms.assetid: 72f54a45-dbe6-4bb4-8c99-e879a27368e5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cba4eb2b76d7057a5ed66a35342a79615cb8539f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934824"
---
# <a name="icordebugeval2callparameterizedfunction-method"></a>ICorDebugEval2::CallParameterizedFunction メソッド
コンス トラクターはクラス内にネストすることができますが、指定された、ICorDebugFunction への呼び出しを設定<xref:System.Type>パラメーター、または自体がかかる<xref:System.Type>パラメーター。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CallParameterizedFunction (  
    [in] ICorDebugFunction     *pFunction,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pFunction`  
 [in]ポインター、`ICorDebugFunction`に呼び出される関数を表すオブジェクト。  
  
 `nTypeArgs`  
 [in]関数が受け取る引数の数。  
  
 `ppTypeArgs`  
 [in]関数の引数を表す ICorDebugType オブジェクトを指す各ポインターの配列。  
  
 `nArgs`  
 [in]関数に渡された値の数。  
  
 `ppArgs`  
 [in]関数の引数の値を表す ICorDebugValue オブジェクトを指す各ポインター、配列が渡されます。  
  
## <a name="remarks"></a>Remarks  
 `CallParameterizedFunction` ように、 [icordebugeval::callfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)関数は、型パラメーターを持つクラスの内部で可能性があります、点がかかる場合があります自体の型パラメーター、またはその両方です。 型引数は、クラスのしてから、関数は、まず指定しないでください。  
  
 関数は、別のアプリケーション ドメインでは、遷移が発生します。 ただし、すべての型と値の引数は、対象のアプリケーション ドメインである必要があります。  
  
 関数の評価は、限られたシナリオでのみ実行できます。 場合`CallParameterizedFunction`または`ICorDebugEval::CallFunction`失敗した場合、返された HRESULT はエラーの最も一般的な考えられる理由を示します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
