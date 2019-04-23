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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089239"
---
# <a name="icordebugprocess5-interface"></a>ICorDebugProcess5 インターフェイス
管理対象のオブジェクトのガベージ コレクションに関する情報を提供する、マネージ ヒープへのアクセスをサポートするために ICorDebugProcess インターフェイスを拡張し、デバッガーがかどうかを判断するには、アプリケーションのローカル ネイティブ イメージ キャッシュからイメージを読み込みます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnableNGENPolicy メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|アプリケーションがマネージ デバッガーで実行中にネイティブ イメージを読み込む方法を決定する値を設定します。|  
|[EnumerateGCReferences メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|プロセスでガベージ コレクトされるすべてのオブジェクトの列挙子を取得します。|  
|[EnumerateHandles メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|プロセスでオブジェクト ハンドルの列挙子を取得します。|  
|[EnumerateHeap メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|マネージ ヒープのオブジェクトの列挙子を取得します。|  
|[EnumerateHeapRegions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|マネージ ヒープの領域の列挙子を取得します。|  
|[GetArrayLayout メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|メモリ内配列のレイアウトに関する情報を取得します。|  
|[GetGCHeapInformation メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|ポインターを取得、 [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md)マネージ ヒープ上でガベージ コレクトされるオブジェクトに関する情報を含む構造体。|  
|[GetObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|マネージ ヒープにオブジェクトへのポインターを取得します。|  
|[GetTypeFields メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|その型の識別子に基づく型のフィールド情報を格納する配列にポインターを取得します。|  
|[GetTypeForTypeID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|その型の識別子に基づくオブジェクトに関する情報を提供する型のオブジェクトを取得します。|  
|[GetTypeID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|指定したアドレスにオブジェクトの種類の識別子を取得します。|  
|[GetTypeLayout メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|その型の識別子に基づくメモリ内のオブジェクトのレイアウトに関する情報を取得します。|  
  
## <a name="remarks"></a>Remarks  
 このインターフェイスは ICorDebugProcess、ICorDebugProcess2、論理的に拡張し、 [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)インターフェイス。  
  
> [!NOTE]
>  このインターフェイスは、別のコンピューターまたは別のプロセスでのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
