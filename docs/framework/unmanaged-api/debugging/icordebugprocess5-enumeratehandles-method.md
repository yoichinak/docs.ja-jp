---
title: ICorDebugProcess5::EnumerateHandles メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129676"
---
# <a name="icordebugprocess5enumeratehandles-method"></a>ICorDebugProcess5::EnumerateHandles メソッド
プロセス内のオブジェクトハンドルの列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a>パラメーター  
 `types`  
 からコレクションに含めるハンドルの種類を指定する[Corgcreの](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)値のビットごとの組み合わせ。  
  
 `ppENum`  
 入出力ガベージコレクションの対象となるオブジェクトの列挙子[である、](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)ツールのアドレスへのポインターです。  
  
## <a name="remarks"></a>Remarks  
 `EnumerateHandles` は、ハンドルテーブルの検査をサポートするヘルパー関数です。 これは[ICorDebugProcess5:: EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)メソッドに似ていますが、すべてのオブジェクトがガベージコレクトされるよう[に、すべて](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)のオブジェクトを使用してすべてのオブジェクトを作成するのではなく、からハンドルを持つオブジェクトのみを含むようにする点が異なります。ハンドルテーブル。  
  
 `types` パラメーターは、コレクションに含めるハンドルの種類を指定します。 `types`、次の3つのメンバーのいずれかを[Corgcreの型](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)の列挙体にすることができます。  
  
- `CorHandleStrongOnly` (厳密な参照へのハンドルのみ)。  
  
- `CorHandleWeakOnly` (弱参照のみを処理します)。  
  
- `CorHandleAll` (すべてのハンドル)。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
