---
title: StackTrace_SimpleContext 構造体
ms.date: 03/30/2017
api_name:
- StackTrace_SimpleContext
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- SimpleContext
helpviewer_keywords:
- SimpleContext structure [.NET Framework debugging]
- StackTrace_SimpleContext structure [.NET Framework debugging]
ms.assetid: d4cef11f-a8ca-49bc-a1b8-6631f9e28f3e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0625dc72d44485dbb69b42cba5387085d1862bb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986532"
---
# <a name="stacktracesimplecontext-structure"></a>StackTrace_SimpleContext 構造体
完全な `CONTEXT` 構造の代わりに使用できる単純なコンテキストを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
struct StackTrace_SimpleContext  
{  
    ULONG64 StackOffset;       // ESP on x86  
    ULONG64 FrameOffset;       // EBP on x86  
    ULONG64 InstructionOffset; // EIP on x86  
};  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`StackOffset`|スタック ポインター、または x86 enter スタック ポインター (ESP) プラットフォーム。|  
|`FrameOffset`|フレームのオフセット、または x86 EBP レジスタのプラットフォームです。|  
|`InstructionOffset`|命令ポインター、または x86 enter 命令ポインター (EIP) プラットフォーム。|  
  
## <a name="remarks"></a>Remarks  
 使用できます必要に応じてスタック トレース関数は、通常、アドレス、フレームのオフセット、およびスタック アドレスのみを返す必要があります、ため、`SimpleContext`構造ではなく、大規模な`CONTEXT`構造体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** SOS_Stacktrace.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
