---
title: ICorDebugILFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c60d7685de1e9a1d4f631ad1fba53b981829f58
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988586"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame インターフェイス

Microsoft intermediate language (MSIL) コードのスタック フレームを表します。 このインターフェイスは、ICorDebugFrame インターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|命令ポインターを指定したオフセット位置に設定しても安全であるかどうかを示す値を取得します。|  
|[EnumerateArguments メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|このフレームで、引数の列挙子を取得します。|  
|[EnumerateLocalVariables メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|このフレームでローカル変数の列挙子を取得します。|  
|[GetArgument メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|この MSIL のスタック フレーム内には、指定された引数の値を取得します。|  
|[GetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|命令ポインターの値と命令ポインターの値の取得方法を示すビットごとの組み合わせ値を取得します。|  
|[GetLocalVariable メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|この MSIL のスタック フレーム内には、指定されたローカル変数の値を取得します。|  
|[GetStackDepth メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|実装されていません。|  
|[GetStackValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|実装されていません。|  
|[SetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|MSIL コード内の指定したオフセット位置に、命令ポインターを設定します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugILFrame`インターフェイスは特殊な ICorDebugFrame インターフェイスです。 使用される MSIL コードのフレームまたは・ イン タイム (JIT) コンパイル済みのフレーム。 JIT コンパイルされたフレームでは、両方を実装、`ICorDebugILFrame`インターフェイスと ICorDebugNativeFrame インターフェイス。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
