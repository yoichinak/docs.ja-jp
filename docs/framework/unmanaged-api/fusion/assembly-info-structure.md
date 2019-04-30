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
ms.openlocfilehash: bae19ec18c54eccc7aa54d2d3a006f36ba8ab762
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61985960"
---
# <a name="assemblyinfo-structure"></a>ASSEMBLY_INFO 構造体
グローバル アセンブリ キャッシュに登録されているアセンブリに関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`cbAssemblyInfo`|構造体のバイト単位のサイズ。 このフィールドは、将来の機能拡張予約されています。|  
|`dwAssemblyFlags`|アセンブリのインストールの詳細を示すフラグです。 次の値がサポートされています。<br /><br /> -ASSEMBLYINFO_FLAG_INSTALLED 値、アセンブリがインストールされていることを示します。 .NET Framework の現在のバージョンが常に設定`dwAssemblyFlags`この値にします。<br />-ASSEMBLYINFO_FLAG_PAYLOADRESIDENT 値、アセンブリが常駐ペイロードであることを示します。 .NET Framework の現在のバージョンを設定しません`dwAssemblyFlags`この値にします。|  
|`uliAssemblySizeInKB`|アセンブリに含まれるファイルの合計サイズ。|  
|`pszCurrentAssemblyPathBuf`|マニフェスト ファイルに、現在のパスを保持する文字列バッファーへのポインター。 パスの末尾に null 文字を使用する必要があります。|  
|`cchBuf`|Null の終端文字を含め、ワイド文字の数を`pszCurrentAssemblyPathBuf`が含まれています。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
