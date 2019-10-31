---
title: ICoreClrDebugTarget::EnumProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 4d1404e3f7565ee26edd94e059b7f01f8edd4dd6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121843"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses メソッド
リモート コンピューターで実行されているプロセスを列挙します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pcProcs`  
 [out] `ppProcs` に返されるプロセス数。 この値は 0 (ゼロ) になる可能性もあります。  
  
 `ppProcs`  
 入出力リモートコンピューター上で実行されているプロセスを表す[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)構造体の配列。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 成功。  
  
 E_OUTOFMEMORY  
 `ppProcs`  用に十分なメモリを割り当てることができません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="remarks"></a>Remarks  
 このメソッドによって割り当てられたメモリを解放するには、 [ICoreClrDebugTarget:: FreeMemory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)メソッドを呼び出します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Coreclrremoteデバッグインターフェイス .h  
  
 **ライブラリ:** mscordbi_macx86  
  
 **.NET Framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICoreClrDebugTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
