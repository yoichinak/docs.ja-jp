---
title: ICorDebugAppDomain::GetName メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetName
helpviewer_keywords:
- ICorDebugAppDomain::GetName method [.NET Framework debugging]
- GetName method, ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: 02c596d7-00b0-4e2c-856b-5425158fcefd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7939f7b1c0c725bb4e8c642bc38121dd755da5e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785139"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName メソッド
アプリケーション ドメインの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchName`  
 [in] `szName` 配列のサイズ。 この値をクエリ モードでこのメソッドを配置する 0 に設定します。  
  
 `pcchName`  
 [out]名前またはで実際に返される文字数のサイズへのポインター`szName`します。 クエリ モードでこの値により、バッファーのサイズを呼び出し元に名前を割り当てられません。  
  
 `szName`  
 [out]アプリケーション ドメインの名前を格納する配列。  
  
## <a name="remarks"></a>Remarks  
 デバッガーは、`GetName`メソッドを 1 回、名前に必要なバッファーのサイズを取得します。 デバッガーはバッファーを割り当てたし、メソッドを呼び出して、2 回バッファーを埋めます。 最初の呼び出しで、名前のサイズを取得すると呼びます*クエリ モード*します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
