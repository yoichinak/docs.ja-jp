---
title: ICorDebugFrame::GetStackRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 7a35ce025360e0ec8b7085d68e54548026b7c7fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178908"
---
# <a name="icordebugframegetstackrange-method"></a>ICorDebugFrame::GetStackRange メソッド
このスタック フレームの絶対アドレス範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pStart`  
 [アウト]この`CORDB_ADDRESS``ICorDebugFrame`オブジェクトによって表されるスタック フレームの開始アドレスを指定するを指すポインター。  
  
 `pEnd`  
 [アウト]この`CORDB_ADDRESS``ICorDebugFrame`オブジェクトによって表されるスタック フレームの終了アドレスを指定するを指すポインター。  
  
## <a name="remarks"></a>解説  
 スタックのアドレス範囲は、複数のデバッグエンジンから収集されたインターリーブスタックトレースをつなぎ合わせる場合に便利です。 数値範囲は、スタック フレームの内容に関する情報を提供しません。 スタック フレームの位置を比較する場合にのみ意味があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
