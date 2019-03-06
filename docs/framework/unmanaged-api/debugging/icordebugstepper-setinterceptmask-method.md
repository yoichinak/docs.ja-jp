---
title: ICorDebugStepper::SetInterceptMask メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25a9d287e6520f1fc7826d85dfbcd8e9a6da22f7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481069"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask メソッド
ステップ インはコードの種類を指定する値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mask`  
 [in]コードの種類を指定する CorDebugIntercept 列挙型の値の組み合わせ。  
  
## <a name="remarks"></a>Remarks  
 インターセプターのビットが設定されている場合、特定の種類のコードをインターセプトが発生した場合に、ステッパが終了します。 ビットがオフの場合は傍受のコードはスキップされます。  
  
 `SetInterceptMask`メソッドがありますで予期しない相互作用[icordebugstepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (ユーザーの観点から)。 たとえば場合、のみ表示されます (は、非内部) クラスの初期化コードの部分にマッピング情報が不足していますと STOP_NO_MAPPING_INFO が設定されていない (を参照してください、 [icordebugstepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)メソッドとCorDebugUnmappedStop 列挙型)、ステッパ、ステップ オーバーはクラスの初期化します。 既定の INTERCEPT_NONE 値だけで、`CorDebugIntercept`列挙型が使用されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
