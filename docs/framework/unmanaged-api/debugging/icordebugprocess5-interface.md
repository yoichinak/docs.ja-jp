---
title: ICorDebugProcess5 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: 64fb60abf4f5730dbc15204dbc034b08cacefab9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121247"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 インターフェイス
は、アプリケーションインターフェイスを拡張して、マネージヒープへのアクセスをサポートし、マネージオブジェクトのガベージコレクションに関する情報を提供し、デバッガーがアプリケーションのローカルネイティブイメージキャッシュからイメージを読み込むかどうかを判断します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnableNGENPolicy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|マネージデバッガーで実行中にアプリケーションがネイティブイメージを読み込む方法を決定する値を設定します。|  
|[EnumerateGCReferences メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|プロセスでガベージコレクトされるすべてのオブジェクトの列挙子を取得します。|  
|[EnumerateHandles メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|プロセス内のオブジェクトハンドルの列挙子を取得します。|  
|[EnumerateHeap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|マネージヒープ上のオブジェクトの列挙子を取得します。|  
|[EnumerateHeapRegions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|マネージヒープの領域の列挙子を取得します。|  
|[GetArrayLayout メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|メモリ内の配列のレイアウトに関する情報を取得します。|  
|[GetGCHeapInformation メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|マネージヒープでガベージコレクトされるオブジェクトに関する情報を格納している[COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)構造体へのポインターを取得します。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|マネージヒープ上のオブジェクトへのポインターを取得します。|  
|[GetTypeFields メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|型の識別子に基づいて、型のフィールド情報を格納している配列へのポインターを取得します。|  
|[GetTypeForTypeID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|型識別子に基づいてオブジェクトに関する情報を提供する型オブジェクトを取得します。|  
|[GetTypeID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|指定したアドレスにあるオブジェクトの型識別子を取得します。|  
|[GetTypeLayout メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|型識別子に基づいて、メモリ内のオブジェクトのレイアウトに関する情報を取得します。|  
  
## <a name="remarks"></a>コメント  
 このインターフェイスは、ICorDebugProcess、ICorDebugProcess2、および [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) の各インターフェイスを論理的に拡張します。  
  
> [!NOTE]
> このインターフェイスは、別のコンピューターまたは別のプロセスからのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
