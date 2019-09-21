---
title: ICorDebugChain インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93ada40bd88e53cd06f5e8d8136b2d527d7741e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969307"
---
# <a name="icordebugchain-interface"></a>ICorDebugChain インターフェイス

物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumerateFrames メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|チェーン内のすべてのマネージスタックフレームが格納された列挙子を取得します。これは、最新のフレームから始まります。|  
|[GetActiveFrame メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|チェーンのアクティブな (つまり、最新の) フレームを取得します。|  
|[GetCallee メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|このチェーンによって呼び出されたチェーンを取得します。|  
|[GetCaller メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|このチェーンを呼び出したチェーンを取得します。|  
|[GetContext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|実装されていません。|  
|[GetNext メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|スレッドの次のフレームのチェーンを取得します。|  
|[GetPrevious メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|スレッドの前のフレームのチェーンを取得します。|  
|[GetReason メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|この呼び出しチェーンの genesis の理由を取得します。|  
|[GetRegisterSet メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|このチェーンのアクティブな部分のレジスタセットを取得します。|  
|[GetStackRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|このチェーンのスタックセグメントのアドレス範囲を取得します。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|この呼び出しチェーンが含まれている物理スレッドを取得します。|  
|[IsManaged メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|このチェーンでマネージコードが実行されているかどうかを示す値を取得します。|  
  
## <a name="remarks"></a>Remarks  
 チェーン内のスタックフレームは、連続したスタック領域を占有し、同じスレッドとコンテキストを共有します。 チェーンは、マネージコードチェーンまたはアンマネージコードチェーンを表すことができます。 空`ICorDebugChain`のインスタンスは、アンマネージコードチェーンを表します。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
