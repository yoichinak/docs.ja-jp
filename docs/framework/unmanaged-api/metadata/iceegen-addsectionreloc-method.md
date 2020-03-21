---
title: ICeeGen::AddSectionReloc メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176111"
---
# <a name="iceegenaddsectionreloc-method"></a>ICeeGen::AddSectionReloc メソッド
コード ベースに .reloc 命令を追加します。  
  
 このメソッドは廃止され、使用しないでください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `section`  
 [in]reloc 命令を追加するメモリ内コードのセクション。  
  
 `offset`  
 [in]セクションのオフセット。  
  
 `relativeTo`  
 [in]参照先の`offset`セクション。  
  
 `relocType`  
 [in]追加する[.reloc](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md)命令の種類を示す、1 つの値です。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
