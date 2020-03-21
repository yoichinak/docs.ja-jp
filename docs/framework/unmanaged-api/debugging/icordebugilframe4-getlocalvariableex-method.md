---
title: ICorDebugILFrame4::GetLocalVariableEx メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetCodeEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 0c8676f8-ca0d-4998-b64d-fefac7e38912
topic_type:
- apiref
ms.openlocfilehash: ee263e8c49cd6da7278bd2299557336629720d2f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178780"
---
# <a name="icordebugilframe4getlocalvariableex-method"></a>ICorDebugILFrame4::GetLocalVariableEx メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 この中間言語 (IL) スタック フレーム内の指定されたローカル変数の値を取得して、オプションでプロファイラー ReJIT インストルメンテーションに追加された変数にアクセスできます。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetLocalVariableEx(  
   [in] ILCodeKind flags,
   [in] DWORD dwIndex,
   [out] ICorDebugValue **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `flags`  
 [in]プロファイラー ReJIT インストルメンテーションに追加された変数をフレームに含めるかどうかを指定する[ILCodeKind](ilcodekind-enumeration.md)列挙メンバー。  
  
 `dwIndex`  
 [in] IL スタック フレーム内のローカル変数のインデックス。  
  
 `ppValue`  
 [アウト]取得した値を表す "ICorDebugValue" オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>解説  
 このメソッドは、オプションでプロファイラー ReJIT インストルメンテーションで追加された変数にアクセスする点を除いて[、GetLocalVariable](icordebugilframe-getlocalvariable-method.md)メソッドに似ています。 の値を指定して`flags`このメソッド`ILCODE_ORIGINAL_IL`を呼び出すことは[、GetLocalVariable](icordebugilframe-getlocalvariable-method.md)を呼び出すことと同じです。メソッドに追加のローカル変数がインストルメント化されている場合、これらの変数にはアクセスできません。 `ILCODE_REJIT_IL` は、デバッガーがプロファイラー ReJIT インストルメンテーションに追加されたローカル変数にアクセスできるようにします。 IL がインストルメントされていない場合、メソッドは `E_INVALIDARG` を返します。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugILFrame4 インターフェイス](icordebugilframe4-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
- [ReJIT:ハウツーガイド](https://docs.microsoft.com/archive/blogs/davbr/rejit-a-how-to-guide)
