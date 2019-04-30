---
title: ICorDebugThread2::GetActiveFunctions メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed13f78d5a1f6d54b12c86613715f4878a521bfa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993968"
---
# <a name="icordebugthread2getactivefunctions-method"></a>ICorDebugThread2::GetActiveFunctions メソッド
このスレッドのフレームのそれぞれに、アクティブな関数についての情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cFunctions`  
 [in] `pFunctions` 配列のサイズ。  
  
 `pcFunctions`  
 [out]返されるオブジェクトの数へのポインター、`pFunctions`配列。 返されるオブジェクトの数は、スタック上のマネージ フレームの数と等しくなります。  
  
 `pFunctions`  
 [入力、出力]このスレッドのフレームでアクティブな関数についての情報を含む、COR_ACTIVE_FUNCTION オブジェクトの配列。  
  
 最初の要素は、リーフ フレームとスタックのルートに戻る ために使用されます。  
  
## <a name="remarks"></a>Remarks  
 場合`pFunctions`が null の入力で`GetActiveFunctions`スタック上にある関数の数のみを返します。 つまり場合、`pFunctions`が入力で null`GetActiveFunctions`値を返しますでのみ`pcFunctions`します。  
  
 `GetActiveFunctions`メソッドは、最適化として、スタック トレース内のフレームから同じ情報の取得をありありました ICorDebugILFrame オブジェクトに完全なスタック トレース フレームのみが含まれています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
