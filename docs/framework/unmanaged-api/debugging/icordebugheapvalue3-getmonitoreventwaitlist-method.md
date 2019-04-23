---
title: ICorDebugHeapValue3::GetMonitorEventWaitList メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3.GetMonitorEventWaitList
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList
helpviewer_keywords:
- ICorDebugHeapValue3::GetMonitorEventWaitList method [.NET Framework debugging]
- GetMonitorEventWaitList method [.NET Framework debugging]
ms.assetid: 035a9035-ac66-4953-b48a-99652b42b7fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db331d75244d59aacf2207a6b83a3f337a64b989
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59102792"
---
# <a name="icordebugheapvalue3getmonitoreventwaitlist-method"></a>ICorDebugHeapValue3::GetMonitorEventWaitList メソッド
モニター ロックに関連付けられているイベントをキューに置かれたスレッドの順序付きリストを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMonitorEventWaitList (  
    [out] ICorDebugThreadEnum **ppThreadEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppThreadEnum`  
 [out]スレッドの順序付きリストを提供する ICorDebugThreadEnum 列挙子。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|The list is not empty.|  
|S_FALSE|リストが空です。|  
  
## <a name="exceptions"></a>例外  
  
## <a name="remarks"></a>Remarks  
 一覧の最初のスレッドは、次回の呼び出しからリリースされる最初のスレッド<xref:System.Threading.Monitor.Pulse%28System.Object%29?displayProperty=nameWithType>します。 次の呼び出しでは、上の一覧で、次のスレッドが解放されます。  
  
 リストが空でない場合、このメソッドは、S_OK を返します。 リストが空の場合、メソッドは S_FALSE; を返しますこの場合、列挙型がまだ有効で空ですが。  
  
 いずれの場合も、列挙インターフェイスは、現在の同期状態の期間に対してのみ使用可能です。 ただし、スレッドが終了するまでは、そこから割り当てられたスレッドのインターフェイスは有効です。  
  
 場合`ppThreadEnum`有効なポインターでない、結果は未定義です。  
  
 モニタのスレッドが待機している場合に、これを特定できないように、エラーが発生した場合、メソッドは失敗を示す HRESULT を返します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
