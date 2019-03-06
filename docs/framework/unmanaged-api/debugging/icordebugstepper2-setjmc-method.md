---
title: ICorDebugStepper2::SetJMC メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2.SetJMC
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2::SetJMC
helpviewer_keywords:
- ICorDebugStepper2::SetJMC method [.NET Framework debugging]
- SetJMC method [.NET Framework debugging]
ms.assetid: f5cdc135-6db4-4b32-9dd1-260ec58b774f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 129bf04a097b2019b080f813bf049d41b501f8fd
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474216"
---
# <a name="icordebugstepper2setjmc-method"></a>ICorDebugStepper2::SetJMC メソッド
この ICorDebugStepper のステップは、アプリケーションの開発者が作成したコードからのみかどうかを指定する値を設定します。 このプロセスは、マイ コード (のみ JMC) のデバッグとも呼ばれます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetJMC (  
    [in] BOOL    fIsJMCStepper  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fIsJMCStepper`  
 [in]設定`true`だけは、アプリケーションの開発者が作成した。 それ以外の場合、に設定するコードをステップ実行する`false`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
