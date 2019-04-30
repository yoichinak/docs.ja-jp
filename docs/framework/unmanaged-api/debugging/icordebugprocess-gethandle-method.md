---
title: ICorDebugProcess::GetHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d81564a34ed8e7ef75840e3a174661c36f5411
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994496"
---
# <a name="icordebugprocessgethandle-method"></a>ICorDebugProcess::GetHandle メソッド
プロセスを識別するハンドルを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a>パラメーター  
 `phProcessHandle`  
 [out]ポインター、`HPROCESS`はプロセスを識別するハンドル。  
  
## <a name="remarks"></a>Remarks  
 取得されたハンドルは、デバッグのインターフェイスが所有します。 デバッガーでは、使用する前に、ハンドルを複製する必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
