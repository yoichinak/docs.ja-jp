---
title: ICoreClrDebugTarget インターフェイス
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget interface
- Silverlight, remote debugging
ms.assetid: 7cfaee76-e284-4a66-a431-8e33f0f60038
topic_type:
- apiref
ms.openlocfilehash: 83afe121b6bf0de3c5542695e38b6605db7a8b6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121817"
---
# <a name="icoreclrdebugtarget-interface"></a>ICoreClrDebugTarget インターフェイス
参照カウントを制御し、プロセスを列挙し、リモートの Macintosh Silverlight ターゲットにアタッチされているデバッガーに関連付けられているメモリを解放するメソッドを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
class ICoreClrDebugTarget {  
      HRESULT EnumProcesses (  
          [out] DWORD*                    pcProcs,  
          [out] CoreClrDebugProcInfo**    ppProcs  
      );  
  
      HRESULT EnumRuntimes (  
      [in]  DWORD                      dwInternalProcessID,  
      [out] DWORD*                     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**  ppRuntimes  
      );  
  
      void FreeMemory (  
      [in] void*      pMemory  
    );  
};  
```  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ICoreClrDebugTarget::EnumProcesses メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumprocesses-method.md)|リモート コンピューターで実行されているプロセスを列挙します。|  
|[ICoreClrDebugTarget::EnumRuntimes メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-enumruntimes-method.md)|リモートコンピューター上の指定されたプロセスの共通言語ランタイム (CLRs) を列挙します。|  
|[ICoreClrDebugTarget::FreeMemory メソッド](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-freememory-method.md)|このクラスの列挙メソッドによって割り当てられたメモリを解放します。|  
  
## <a name="remarks"></a>Remarks  
 現在、この機能は、リモートの Macintosh コンピューターで実行されている Silverlight ベースのアプリケーションターゲットをデバッグする場合にのみサポートされます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Coreclrremoteデバッグインターフェイス .h  
  
 **ライブラリ:** mscordbi_macx86  
  
 **.NET Framework のバージョン:** 3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
