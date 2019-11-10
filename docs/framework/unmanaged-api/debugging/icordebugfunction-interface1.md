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
ms.openlocfilehash: eb2b1e218314be01898ce90c4378fb713f9bf6ba
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137848"
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
|[GetLocalVarSigToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|この `ICorDebugFunction` インスタンスによって表される関数のローカル変数シグネチャのメタデータトークンを取得します。|  
|[GetModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が定義されているモジュールを取得します。|  
|[GetNativeCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|この関数のネイティブコードを取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|この関数のメタデータトークンを取得します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugFunction` インターフェイスは、ジェネリック型パラメーターを持つ関数を表していません。 たとえば、`ICorDebugFunction` インスタンスは `Func<T>` を表しますが `Func<string>`は表しません。 [ICorDebugILFrame2:: EnumerateTypeParameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)を呼び出して、ジェネリック型パラメーターを取得します。  
  
 メソッドのメタデータトークン、`mdMethodDef`、およびメソッドの `ICorDebugFunction` オブジェクト間のリレーションシップは、関数でエディットコンティニュが許可されているかどうかによって異なります。  
  
- 関数でエディットコンティニュが許可されていない場合、`ICorDebugFunction` オブジェクトと `mdMethodDef` トークンの間には一対一のリレーションシップが存在します。 つまり、関数は、1つの `ICorDebugFunction` オブジェクトと1つの `mdMethodDef` トークンを持ちます。  
  
- 関数でエディットコンティニュが許可されている場合、`ICorDebugFunction` オブジェクトと `mdMethodDef` トークンの間に多対一のリレーションシップが存在します。 つまり、関数は、関数の各バージョンに対して1つずつ `ICorDebugFunction`のインスタンスを多数持つことができますが、`mdMethodDef` トークンは1つだけです。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
