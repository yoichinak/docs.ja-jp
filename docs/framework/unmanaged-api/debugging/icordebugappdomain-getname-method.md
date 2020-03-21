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
ms.openlocfilehash: 45d27fca888bdabedf197525c63dbd03af7ba1ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179090"
---
# <a name="icordebugappdomaingetname-method"></a>ICorDebugAppDomain::GetName メソッド
アプリケーション ドメインの名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32           cchName,  
    [out] ULONG32           *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
         WCHAR              szName[]  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cchName`  
 [in] `szName` 配列のサイズ。 このメソッドをクエリ モードにするには、この値を 0 に設定します。  
  
 `pcchName`  
 [アウト]名前のサイズ、または 実際に返される文字数へのポインター `szName`。 クエリ モードでは、この値を使用すると、呼び出し元は名前に割り当てるバッファの大きさを知ることができます。  
  
 `szName`  
 [アウト]アプリケーション ドメインの名前を格納する配列。  
  
## <a name="remarks"></a>解説  
 デバッガーは、名前`GetName`に必要なバッファーのサイズを取得するメソッドを 1 回呼び出します。 デバッガーは、バッファーを割り当てるし、バッファーを埋めるために、メソッドを呼び出します。 名前のサイズを取得する最初の呼び出しは、クエリ*モード*と呼ばれます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
