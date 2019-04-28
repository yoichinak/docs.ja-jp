---
title: AssemblyComparisonResult 列挙型
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914501"
---
# <a name="assemblycomparisonresult-enumeration"></a>AssemblyComparisonResult 列挙型
によって決定される 2 つのアセンブリ id の等価性を示す、 [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)関数。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,   
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,    
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,      
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,    
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion    
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー名|説明|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|すべてのアセンブリがフィールド比較一致していることを示します。|  
|`ACR_EquivalentFXUnified`|あるアセンブリ同等と見なされる、共通言語ランタイム (CLR) バージョンの統合、.NET Framework version 2.0 のアセンブリ バージョン番号に基づくことを示します。|  
|`ACR_EquivalentPartialFXUnified`|.NET Framework 2.0 のアセンブリ バージョン番号の CLR 統合に基づくアセンブリは部分的に一致することを示します。|  
|`ACR_EquivalentPartialMatch`|部分的に一致するアセンブリを示します。|  
|`ACR_EquivalentPartialUnified`|部分的に一致するバージョン番号の従来の統合に基づくアセンブリを示します。|  
|`ACR_EquivalentPartialWeakNamed`|単純な名前のアセンブリは部分的に一致することを示します。|  
|`ACR_EquivalentUnified`|あるアセンブリ同等と見なされる以前のバージョンの .NET Framework のバージョン番号の CLR 統合に基づくことを示します。|  
|`ACR_EquivalentWeakNamed`|一致する 2 つの単に名前付きアセンブリのバージョン番号が無視されたことを示します。|  
|`ACR_NonEquivalent`|2 つのアセンブリ間で一致が発生しなかったことを示します。|  
|`ACR_NonEquivalentPartialVersion`|2 つのアセンブリが、そのバージョン番号は、部分的に一致を除くと一致することを示します。|  
|`ACR_NonEquivalentVersion`|2 つのアセンブリが一致しないバージョン番号を取得するには、以外と一致することを示します。|  
|`ACR_Unknown`|不一致の理由がわからないことを示します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [CompareAssemblyIdentity 関数](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [Fusion 列挙型](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
