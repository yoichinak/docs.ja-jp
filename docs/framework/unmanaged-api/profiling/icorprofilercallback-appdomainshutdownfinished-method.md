---
title: ICorProfilerCallback::AppDomainShutdownFinished メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainShutdownFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainShutdownFinished
helpviewer_keywords:
- AppDomainShutdownFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainShutdownFinished method [.NET Framework profiling]
ms.assetid: 52794819-0a59-4bb1-a265-0f158cd5cd65
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16973fe322a0fbd7a2433cd94982df04eb13dc50
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468729"
---
# <a name="icorprofilercallbackappdomainshutdownfinished-method"></a>ICorProfilerCallback::AppDomainShutdownFinished メソッド
アプリケーション ドメインが、プロセスからアンロードされたことをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AppDomainShutdownFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>パラメーター  
 `appDomainId`  
 [in]アプリケーションのアセンブリが格納されているドメインを識別します。  
  
 `hrStatus`  
 [in]かどうか、アプリケーション ドメインがアンロードされた正常を示す HRESULT。  
  
## <a name="remarks"></a>Remarks  
 値`appDomainId`は後の情報の要求は無効です、 [icorprofilercallback::appdomainshutdownstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)メソッドを返します。  
  
 アプリケーション ドメインのアンロードの一部が後に続ける可能性があります、`AppDomainCreationFinished`コールバック。 エラーの HRESULT で`hrStatus`失敗を示します。 ただし、成功 HRESULT で`hrStatus`のみにアプリケーション ドメインをアンロードの最初の部分が成功したことを示します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
