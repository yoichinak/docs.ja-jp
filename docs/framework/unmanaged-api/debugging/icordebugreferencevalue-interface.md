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
ms.openlocfilehash: d6575acfb1f75cbc8e3d59ddca5fea0953274cf2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782955"
---
# <a name="icordebugreferencevalue-interface"></a>ICorDebugReferenceValue インターフェイス
オブジェクトへの参照である値を管理するメソッドを提供します。 (つまり、このインターフェイスはポインターを管理するメソッドを提供します。)このインターフェイスは、"ICorDebugValue"を実装します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Dereference メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereference-method.md)|参照されているオブジェクトを取得します。|  
|[DereferenceStrong メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-dereferencestrong-method.md)|実装されていません。 このメソッドを呼び出さないでください。|  
|[GetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-getvalue-method.md)|参照先オブジェクトの現在のメモリ アドレスを取得します。|  
|[IsNull メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-isnull-method.md)|示す値を取得するかどうかこの`ICorDebugReferenceValue`、null 値の場合は、`ICorDebugReferenceValue`がオブジェクトを指していません。|  
|[SetValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-setvalue-method.md)|現在のメモリ アドレスを設定します。 つまり、このメソッドはこの設定`ICorDebugReferenceValue`オブジェクトを指すようにします。|  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイム (CLR) は、デバッグ対象のプロセスが続行すると、オブジェクトのガベージ コレクションを行うことができます。 ガベージ コレクションは、メモリ内の周りオブジェクトを移動可能性があります。 `ICorDebugReferenceValue`はいずれかと連携してガベージ コレクション、ガベージ コレクション後にその情報が更新またはガベージ コレクションの前に暗黙的に無効にできるようにします。  
  
 `ICorDebugReferenceValue`デバッグ対象のプロセスが続行されるした後にオブジェクトが暗黙的に検証済みにすることがあります。 明示的に解放または公開されるまでは、派生"ICorDebugHandleValue"は無効化されません。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
