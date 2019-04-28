---
title: ICorDebugModule::EnableJITDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.EnableJITDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::EnableJITDebugging
helpviewer_keywords:
- ICorDebugModule::EnableJITDebugging method [.NET Framework debugging]
- EnableJITDebugging method [.NET Framework debugging]
ms.assetid: 0a65e2a4-5bb6-496c-ae6f-40474426b5a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 642c4fd600d10ef89a08aa32bef5c8e7455552c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937177"
---
# <a name="icordebugmoduleenablejitdebugging-method"></a>ICorDebugModule::EnableJITDebugging メソッド
ジャストイン タイム (JIT) コンパイラがこのモジュール内でメソッドのデバッグ情報を保持するかどうかを制御します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnableJITDebugging(  
    [in] BOOL bTrackJITInfo,  
    [in] BOOL bAllowJitOpts  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bTrackJITInfo`  
 [in]この値に設定`true`Microsoft intermediate language (MSIL) のバージョンと、このモジュール内の各メソッドの JIT コンパイルされたバージョン間のマッピング情報を保持するために、JIT コンパイラを有効にします。  
  
 `bAllowJitOpts`  
 [in]この値に設定`true`デバッグの特定の特定の JIT 最適化を使用したコードを生成する、JIT コンパイラを有効にします。  
  
## <a name="remarks"></a>Remarks  
 既定では、デバッガーがアクティブなときに読み込まれているすべてのモジュール、JIT デバッグを有効になっています。 プログラムでを有効または無効にするには、グローバル設定よりも優先されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
