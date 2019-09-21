---
title: ICorDebugAppDomain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12753ab65f9339e8f6c3049bb72755e87464eb1a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963110"
---
# <a name="icordebugappdomain-interface"></a>ICorDebugAppDomain インターフェイス

アプリケーション ドメインをデバッグするためのメソッドを提供します。 このインターフェイスは、というコントロールのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Attach メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-attach-method.md)|デバッガーをアプリケーションドメインにアタッチします。|  
|[EnumerateAssemblies メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|アプリケーションドメイン内のアセンブリの列挙子を取得します。|  
|[EnumerateBreakpoints メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratebreakpoints-method.md)|アプリケーションドメイン内のすべてのアクティブなブレークポイントの列挙子を取得します。|  
|[EnumerateSteppers メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumeratesteppers-method.md)|アプリケーションドメイン内のすべてのアクティブな steppers の列挙子を取得します。|  
|[GetID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getid-method.md)|アプリケーションドメインの一意の ID を取得します。|  
|[GetModuleFromMetaDataInterface メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getmodulefrommetadatainterface-method.md)|指定されたメタデータインターフェイスを持つ、のモジュールオブジェクトを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getname-method.md)|アプリケーションドメインの名前を取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getobject-method.md)|共通言語ランタイム (CLR) アプリケーションドメインへのインターフェイスポインターを取得します。|  
|[GetProcess メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-getprocess-method.md)|アプリケーションドメインを格納しているプロセスを取得します。|  
|[IsAttached メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-isattached-method.md)|デバッガーがアプリケーションドメインにアタッチされているかどうかを判断します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
