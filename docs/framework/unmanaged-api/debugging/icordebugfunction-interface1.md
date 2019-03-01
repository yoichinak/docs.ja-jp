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
ms.openlocfilehash: 0c2a4dc823768b722e9069c411be787a66989b2a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977111"
---
# <a name="icordebugfunction-interface"></a>ICorDebugFunction インターフェイス

マネージド関数またはマネージド メソッドを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateBreakpoint メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-createbreakpoint-method.md)|この関数の先頭にブレークポイントを作成します。|  
|[GetClass メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getclass-method.md)|この関数のメンバーであるクラスを表す ICorDebugClass オブジェクトを取得します。|  
|[GetCurrentVersionNumber メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getcurrentversionnumber-method.md)|この関数に対して行われた最新の編集のバージョン番号を取得します。|  
|[GetILCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getilcode-method.md)|この関数の Microsoft intermediate language (MSIL) コードを取得します。|  
|[GetLocalVarSigToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getlocalvarsigtoken-method.md)|これで表される関数のローカル変数シグネチャのメタデータ トークンを取得`ICorDebugFunction`インスタンス。|  
|[GetModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|この関数が定義されているモジュールを取得します。|  
|[GetNativeCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getnativecode-method.md)|この関数のネイティブ コードを取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-gettoken-method.md)|この関数のメタデータ トークンを取得します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugFunction`インターフェイスがジェネリック型パラメーターを持つ関数を表していません。 たとえば、`ICorDebugFunction`はインスタンスを表します`Func<T>`なく`Func<string>`します。 呼び出す[icordebugilframe 2::enumeratetypeparameters](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-enumeratetypeparameters-method.md)ジェネリック型パラメーターを取得します。  
  
 メソッドのメタデータのトークンの間のリレーションシップ`mdMethodDef`、およびメソッドの`ICorDebugFunction`オブジェクトは、関数の編集と続行を許可するかどうかによって異なります。  
  
-   間で一対一のリレーションシップが存在する場合は、関数、エディット コンティニュは許可されていません、`ICorDebugFunction`オブジェクトと`mdMethodDef`トークンです。 つまり、関数には 1 つ`ICorDebugFunction`オブジェクトと 1 つ`mdMethodDef`トークンです。  
  
-   間で多対一のリレーションシップが存在する場合は、関数では、エディット コンティニュは許可して、`ICorDebugFunction`オブジェクトと`mdMethodDef`トークンです。 つまり、関数は多くのインスタンスのことは`ICorDebugFunction`、関数のバージョンごとに 1 つが、1 つだけ`mdMethodDef`トークンです。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
