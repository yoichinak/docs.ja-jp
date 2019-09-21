---
title: ICorDebugReferenceValue インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue
helpviewer_keywords:
- ICorDebugReferenceValue interface [.NET Framework debugging]
ms.assetid: 2040e2be-119a-4cfb-ae52-b0b6f052665c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 67006603747abd89f1b635c065860dcbe1c47a29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965644"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue インターフェイス
オブジェクトへの参照である値を管理するメソッドを提供します。 (つまり、このインターフェイスには、ポインターを管理するメソッドが用意されています)。このインターフェイスは、"ICorDebugValue" を実装します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dereference メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|参照されているオブジェクトを取得します。|  
|[DereferenceStrong メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|実装されていません。 このメソッドを呼び出さないでください。|  
|[GetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|参照先のオブジェクトの現在のメモリアドレスを取得します。|  
|[IsNull メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|このが null 値であるか`ICorDebugReferenceValue`どうかを示す値を取得します`ICorDebugReferenceValue` 。この値を指定した場合、はオブジェクトをポイントしません。|  
|[SetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|現在のメモリアドレスを設定します。 つまり、このメソッドは、オブジェクト`ICorDebugReferenceValue`を指すようにこれを設定します。|  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイム (CLR) は、デバッグされたプロセスが続行されると、オブジェクトのガベージコレクションを実行する場合があります。 ガベージコレクションでは、メモリ内でオブジェクトを移動できます。 `ICorDebugReferenceValue`はガベージコレクションと連携して、ガベージコレクションの後に情報が更新されるか、ガベージコレクションの前に暗黙的に無効にされます。  
  
 デバッグ`ICorDebugReferenceValue`されたプロセスが続行されると、オブジェクトは暗黙的に無効になる可能性があります。 派生された "の値" は、明示的に解放または公開されるまで無効になりません。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
