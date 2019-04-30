---
title: ICorDebugILFrame2::RemapFunction メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92885d2a6514839a864d6a345dd8af8b07b90c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946524"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction メソッド
新しい Microsoft intermediate language (MSIL) オフセットを指定することで編集された関数を再マップします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `newILOffset`  
 [in]スタック フレームの新しい MSIL オフセット命令ポインターを配置する必要があります。 この値は、シーケンス ポイントである必要があります。  
  
 この値の有効性を確保する、呼び出し元の責任になります。 など、MSIL のオフセットは関数の境界の外側では無効です。  
  
## <a name="remarks"></a>Remarks  
 フレームの関数が編集されている場合、デバッガーを呼び出して、`RemapFunction`フレームの関数の最新バージョンにスワップして実行できるようにするメソッド。 指定の MSIL オフセット、コードの実行が開始されます。  
  
> [!NOTE]
>  呼び出す`RemapFunction`と同様に、呼び出す[icordebugilframe::setip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)、すぐにスレッドのスタック トレースの生成に関連するすべてのデバッグのインターフェイスを無効になります。 これらのインターフェイスを含める[ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)ICorDebugILFrame、ICorDebugInternalFrame、および ICorDebugNativeFrame します。  
  
 `RemapFunction`メソッドは、現在のフレームのコンテキストでのみと、次の場合のいずれかでのみ呼び出すことができます。  
  
- 受領後、 [icordebugmanagedcallback 2::functionremapopportunity](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md)続行されていないコールバック。  
  
- コードの実行のための停止中に、 [icordebugmanagedcallback::editandcontinueremap](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md)このフレームのイベント。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
