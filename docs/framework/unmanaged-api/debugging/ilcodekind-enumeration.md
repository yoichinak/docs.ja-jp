---
title: ILCodeKind 列挙型
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fea08331fffb85c91721d60764bae8bfe8b30e27
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928816"
---
# <a name="ilcodekind-enumeration"></a>ILCodeKind 列挙型
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできません。|  
|`ILCODE_REJIT_IL`|デバッガーは、ReJIT インストルメンテーションからの情報に対してアクセスできます。|  
  
## <a name="remarks"></a>Remarks  
 `ILCodeKind`列挙体のメンバーを[EnumerateLocalVariablesEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)メソッドおよび[getlocalvariables ex](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)メソッドに渡して、デバッガーがプロファイラー rejit インストルメンテーション[に追加された変数にアクセスできるかどうかを判断できます。GetCodeEx](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)メソッド。デバッガーがインストルメント化された IL にアクセスできるかどうかを判断します。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [ICorDebugILFrame4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)
- [ReJITハウツーガイド](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
