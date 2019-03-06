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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb7e64da5002f438198a8389d2d8385d7a4210a4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492709"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a>ICoreClrDebugTarget::EnumProcesses メソッド
リモート コンピューターで実行されているプロセスを列挙します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,   
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pcProcs`  
 [out] `ppProcs` に返されるプロセス数。 この値は 0 (ゼロ) になる可能性もあります。  
  
 `ppProcs`  
 [out]配列の[CoreClrDebugProcInfo](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)リモート コンピューターで実行中のプロセスを表す構造体。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 成功。  
  
 E_OUTOFMEMORY  
 `ppProcs`  用に十分なメモリを割り当てることができません。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 その他のエラーが発生しました。  
  
## <a name="remarks"></a>Remarks  
 このメソッドによって割り当てられたメモリを解放する呼び出し、 [icoreclrdebugtarget::freememory](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CoreClrRemoteDebuggingInterfaces.h  
  
 **ライブラリ:** mscordbi_macx86.dll  
  
 **.NET framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目
- [ICoreClrDebugTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)
