---
title: IAssemblyName::GetDisplayName メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyName.GetDisplayName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName::GetDisplayName
helpviewer_keywords:
- GetDisplayName method, IAssemblyName interface [.NET Framework fusion]
- IAssemblyName::GetDisplayName method [.NET Framework fusion]
ms.assetid: 9a26547a-9a34-4284-a463-78a7d4b496cf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 38f48f2d95829d2c8111065e5f4ede4e43a16d63
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796655"
---
# <a name="iassemblynamegetdisplayname-method"></a>IAssemblyName::GetDisplayName メソッド
この[IAssemblyName](iassemblyname-interface.md)オブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetDisplayName (  
        [out]      LPOLESTR  szDisplayName,  
        [in, out]  LPDWORD   pccDisplayName,  
        [in]       DWORD     dwDisplayFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szDisplayName`  
 入出力参照されたアセンブリの名前を格納している文字列バッファー。  
  
 `pccDisplayName`  
 [入力、出力]Null 終端文字`szDisplayName`を含むワイド文字ののサイズ。  
  
 `dwDisplayFlags`  
 からの`szDisplayName`機能に影響を与える[ASM_DISPLAY_FLAGS](asm-display-flags-enumeration.md)値のビットごとの組み合わせ。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IAssemblyName インターフェイス](iassemblyname-interface.md)
- [Fusion 列挙型](fusion-enumerations.md)
