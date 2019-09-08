---
title: ASSEMBLY_INFO 構造体
ms.date: 03/30/2017
api_name:
- ASSEMBLY_INFO
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASSEMBLY_INFO
helpviewer_keywords:
- ASSEMBLY_INFO structure [.NET Framework fusion]
ms.assetid: b3cbb47c-457f-4083-8895-49562ca99ab8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 390ab4881396bbc01337d087f05b6066153bfed1
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795486"
---
# <a name="assembly_info-structure"></a>ASSEMBLY_INFO 構造体
グローバルアセンブリキャッシュに登録されているアセンブリに関する情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _ASSEMBLY_INFO {  
    ULONG           cbAssemblyInfo;  
    DWORD           dwAssemblyFlags;  
    ULARGE_INTEGER  uliAssemblySizeInKB;  
    LPWSTR          pszCurrentAssemblyPathBuf;  
    ULONG           cchBuf;  
} ASSEMBLY_INFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`cbAssemblyInfo`|構造体のサイズ (バイト単位)。 このフィールドは、将来の拡張のために予約されています。|  
|`dwAssemblyFlags`|アセンブリに関するインストールの詳細を示すフラグ。 次の値がサポートされています。<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED 値。アセンブリがインストールされていることを示します。 .NET Framework の現在のバージョンは、常`dwAssemblyFlags`にこの値に設定されます。<br />-アセンブリがペイロード常駐であることを示す ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 値。 .NET Framework の現在のバージョンでは、 `dwAssemblyFlags`この値には設定されません。|  
|`uliAssemblySizeInKB`|アセンブリに格納されているファイルの合計サイズ (kb 単位)。|  
|`pszCurrentAssemblyPathBuf`|マニフェストファイルへの現在のパスを保持する文字列バッファーへのポインター。 パスの末尾は null 文字である必要があります。|  
|`cchBuf`|を格納している`pszCurrentAssemblyPathBuf` 、null 終端文字を含むワイド文字の数。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion 構造体](fusion-structures.md)
- [グローバル アセンブリ キャッシュ](../../app-domains/gac.md)
