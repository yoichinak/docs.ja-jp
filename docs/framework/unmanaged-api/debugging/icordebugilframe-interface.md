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
ms.openlocfilehash: 01c247f838f66d1a77831755126a5a1f56870c1e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095139"
---
# <a name="icordebugilframe-interface"></a>ICorDebugILFrame インターフェイス

Microsoft 中間言語 (MSIL) コードのスタックフレームを表します。 このインターフェイスは、テキストボックスのインターフェイスのサブクラスです。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CanSetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-cansetip-method.md)|命令ポインターを指定したオフセット位置に安全に設定できるかどうかを示す値を取得します。|  
|[EnumerateArguments メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratearguments-method.md)|このフレーム内の引数の列挙子を取得します。|  
|[EnumerateLocalVariables メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-enumeratelocalvariables-method.md)|このフレーム内のローカル変数の列挙子を取得します。|  
|[GetArgument メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getargument-method.md)|この MSIL スタックフレーム内の指定された引数の値を取得します。|  
|[GetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md)|命令ポインターの値と、命令ポインターの値が取得された方法を示すビットごとの組み合わせ値を取得します。|  
|[GetLocalVariable メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getlocalvariable-method.md)|この MSIL スタックフレーム内の指定したローカル変数の値を取得します。|  
|[GetStackDepth メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackdepth-method.md)|実装されていません。|  
|[GetStackValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getstackvalue-method.md)|実装されていません。|  
|[SetIP メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md)|命令ポインターを MSIL コード内の指定したオフセット位置に設定します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugILFrame` インターフェイスは特殊なテキストフレームインターフェイスです。 これは、MSIL コードフレームまたは just-in-time (JIT) コンパイルフレームに対して使用されます。 JIT でコンパイルされたフレームには、`ICorDebugILFrame` インターフェイスと、テキストフレームインターフェイスの両方が実装されています。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
