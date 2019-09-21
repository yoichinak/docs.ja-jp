---
title: ICorDebugFunction インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction
helpviewer_keywords:
- ICorDebugFunction interface [.NET Framework debugging]
ms.assetid: 783faea9-8083-41c1-b04a-51a81ac4c8f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae65c59efe1d925b5e058e8664d1e093fdfec875
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917204"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction インターフェイス

マネージド関数またはマネージド メソッドを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|この関数の先頭にブレークポイントを作成します。|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|この関数がメンバーとなっているクラスを表す、のオブジェクトを取得します。|  
|[GetCurrentVersionNumber メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|この関数に対して行われた最新の編集のバージョン番号を取得します。|  
|[GetILCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|この関数の MSIL (Microsoft 中間言語) コードを取得します。|  
|[GetLocalVarSigToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|この`ICorDebugFunction`インスタンスによって表される関数のローカル変数シグネチャのメタデータトークンを取得します。|  
|[GetModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が定義されているモジュールを取得します。|  
|[GetNativeCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|この関数のネイティブコードを取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|この関数のメタデータトークンを取得します。|  
  
## <a name="remarks"></a>Remarks  
 インターフェイス`ICorDebugFunction`は、ジェネリック型パラメーターを持つ関数を表していません。 たとえば、 `ICorDebugFunction`インスタンスはを表し`Func<T>`ますが、 `Func<string>`ではありません。 [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)を呼び出して、ジェネリック型パラメーターを取得します。  
  
 メソッドのメタデータトークン、 `mdMethodDef`、およびメソッドの`ICorDebugFunction`オブジェクト間のリレーションシップは、関数でエディットコンティニュが許可されているかどうかによって異なります。  
  
- 関数でエディットコンティニュを使用できない場合は、 `ICorDebugFunction`オブジェクト`mdMethodDef`とトークンの間に一対一のリレーションシップが存在します。 つまり、関数は、1つ`ICorDebugFunction`のオブジェクトと`mdMethodDef` 1 つのトークンを持ちます。  
  
- 関数でエディットコンティニュが許可されている場合は、 `ICorDebugFunction`オブジェクト`mdMethodDef`とトークンの間に多対一のリレーションシップが存在します。 つまり、関数は、関数の各バージョンに`ICorDebugFunction`1 つずつ、1つの`mdMethodDef`トークンのみを含むのインスタンスを多数持つことができます。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
