---
title: ICorDebugILFrame4::GetCodeEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: ef2e4bc0caddd6b13c8dbe8edb59e0673519421b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178793"
---
# <a name="icordebugilframe4getcodeex-method"></a>ICorDebugILFrame4::GetCodeEx メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 このスタック フレームが実行中のコードに対するポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `flags`  
 [in]プロファイラーの ReJIT 要求によって定義された中間言語 (IL) がフレームに含まれるかどうかを指定する[ILCodeKind](ilcodekind-enumeration.md)列挙メンバー。  
  
 `ppCode`  
 [アウト]このスタック フレームが実行しているコードを表す "ICorDebugCode" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  
 このメソッドは、プロファイラーの ReJIT 要求によって定義されたコードにオプションでアクセスする点を除いて[、ICorDebugFrame::GetCode](icordebugframe-getcode-method.md)メソッドに似ています。 の値を指定して`flags`このメソッド`ILCODE_ORIGINAL_IL`を呼び出すことは[、GetCode](icordebugframe-getcode-method.md)を呼び出すことと同じです。メソッドがインストルメント化されている場合、IL はアクセスできません。 `ILCODE_REJIT_IL` を使用するとデバッガーは、プロファイラーの ReJIT 要求で定義された IL にアクセスできます。 IL がインストルメント化`ppCode`されていない場合は**null**になり`S_OK`、メソッドはを返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
- [ReJIT:ハウツーガイド](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
