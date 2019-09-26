---
title: CorDebugCodeInvokeKind 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22eeb8aba318d53efbc699d4492a86b2667bcfff
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274120"
---
# <a name="cordebugcodeinvokekind-enumeration"></a>CorDebugCodeInvokeKind 列挙体
エクスポートされた関数がマネージド コードを呼び出す方法を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|マネージド コードがこのメソッドによって呼び出される場合は、明示的なイベントまたはブレークポイントによって後で配置する必要があります。<br /><br /> または<br /><br /> このメソッドが呼び出すマネージド コードは、停止する簡単な方法がないため、一部を見逃す可能性があります。<br /><br /> または<br /><br /> メソッドがマネージド コードを呼び出さない可能性があります。|  
|`CODE_INVOKE_KIND_RETURN`|このメソッドは、戻り命令を使用してマネージド コードを呼び出します。 ステップ アウトは次のマネージド コードに到達する必要があります。|  
|`CODE_INVOKE_KIND_TAILCALL`|このメソッドは、末尾呼び出しを使用してマネージド コードを呼び出します。 いずれかの呼び出し命令をシングル ステップ実行およびステップ オーバーすると、マネージド コードに到達します。|  
  
## <a name="remarks"></a>コメント  
 この列挙体は、マネージコードのステップ実行に関する情報を提供するために、 [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md)メソッドによって使用されます。  
  
> [!NOTE]
> この列挙型は .NET ネイティブのデバッグ シナリオのみで使用することを目的としています。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](debugging-enumerations.md)
- [デバッグ](index.md)
