---
title: CALL_ID 構造体
ms.date: 03/30/2017
api_name:
- CALL_ID
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- CALL_ID
helpviewer_keywords:
- CALL_ID structure [.NET Framework debugging]
ms.assetid: bfd46324-afec-4782-9c18-586d81fb4740
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6fa729b131d12b2825a2def700fd918ce8acc40
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220176"
---
# <a name="callid-structure"></a>CALL_ID 構造体
デバッガーが呼び出される関数に関する情報を提供します。 参照してください、 [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)インターフェイスの詳細についてはします。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct tagCALL_ID  
{  
    LPCOLESTR       szMachine;  
    DWORD           dwPid;  
    USER_THREAD     *pUserThread;  
    STACK_ADDRESS   addrStackPointer;  
    LPCOLESTR       szEntryPoint;  
    LPCOLESTR       szDestinationMachine;  
} CALL_ID;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`szMachine`|呼び出しを行っているコンピューターを識別します。|  
|`dwPid`|コンピューターのプロセッサを識別します。|  
|`pUserThread`|呼び出しを実行しているスレッドを識別します。|  
|`addrStackPointer`|呼び出し履歴のアドレスを指定します。|  
|`szEntryPoint`|呼び出しのアドレスを指定します。|  
|`szDestinationMachine`|呼び出しを実行するマシンを識別します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** ProtocolNotify2.idl  
  
## <a name="see-also"></a>関連項目

- [INotifySink2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [シンボル ストア診断構造体](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)
