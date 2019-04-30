---
title: ICorDebugFunction::GetNativeCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetNativeCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetNativeCode
helpviewer_keywords:
- GetNativeCode method [.NET Framework debugging]
- ICorDebugFunction::GetNativeCode method [.NET Framework debugging]
ms.assetid: c8a34916-0eef-4987-8d29-c8bcb4be9cf6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb85c4b2c26c136a5f9fc05221a42c4bc99f37f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988703"
---
# <a name="icordebugfunctiongetnativecode-method"></a>ICorDebugFunction::GetNativeCode メソッド
この ICorDebugFunction インスタンスで表される関数のネイティブ コードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetNativeCode (  
    [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppCode`  
 [out]この関数は、Microsoft intermediate language (MSIL) コードの just-in-time (JIT) コンパイルされていない場合は、この関数の場合、または null の場合、ネイティブ コードを表す ICorDebugCode インスタンスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 場合、これによって表される関数`ICorDebugFunction`インスタンス JIT でコンパイルされた複数回、ジェネリック型の場合、`GetNativeCode`ランダムなネイティブ コードのオブジェクトを返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
