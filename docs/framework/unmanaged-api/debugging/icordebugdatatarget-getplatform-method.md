---
title: ICorDebugDataTarget::GetPlatform メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 309c31dacd801f1c46a2d37932124638bc157cd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214028"
---
# <a name="icordebugdatatargetgetplatform-method"></a>ICorDebugDataTarget::GetPlatform メソッド
プロセッサ アーキテクチャと、ターゲット プロセスが実行されているオペレーティング システムを含む、プラットフォームについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pTargetPlatform`  
 [out]ポインターを[CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)ターゲット プラットフォームを表す列挙体。  
  
## <a name="remarks"></a>Remarks  
 `CorDebugPlatformEnum`列挙型の戻り値を使って、 [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)インターフェイス ポインターのサイズ、アドレス空間レイアウト、レジスタ セット、命令の形式、コンテキストのレイアウトなど、ターゲット プロセスの詳細を確認して呼び出し規約。  
  
 `pTargetPlatform`値可能性がありますが、実際のハードウェアを使用して指定する代わりに、ターゲットのエミュレートされるプラットフォームを参照してください。 たとえば、Windows オペレーティング システムの 64 ビット版 Windows (WOW) 環境での Windows で実行されているプロセスを使用する必要があります、`CORDB_PLATFORM_WINDOWS_X86`の値、 [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)列挙体。  
  
 このメソッドは成功する必要があります。 失敗した場合、ターゲット プラットフォームは使用できません。 メソッドは、次の理由で失敗します。  
  
-   ターゲットのエミュレートされているプラットフォームでは使用できません。  
  
-   ターゲット プラットフォームの実際のハードウェアが使用できません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
