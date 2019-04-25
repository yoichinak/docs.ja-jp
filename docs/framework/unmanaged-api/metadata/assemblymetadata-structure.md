---
title: ASSEMBLYMETADATA 構造体
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61905919"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA 構造体
そのバージョンとそのロケール、プロセッサ、およびオペレーティング システムのサポートのレベルを含む、参照先アセンブリに関する情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`usMajorVersion`|参照アセンブリのメジャー バージョン番号。 この値は、0 にすることはできません。 場合のすべてのビット`usMajorVersion`メジャー バージョンが指定されていない、設定されます。|  
|`usMinorVersion`|参照アセンブリのマイナー バージョン番号。 この値は、0 にすることはできません。 場合のすべてのビット`usMinorVersion`マイナー バージョンが指定されていない、設定されます。|  
|`usBuildNumber`|参照アセンブリのビルド番号。 この値は、0 にすることはできません。 場合のすべてのビット`usBuildNumber`は設定されて、ビルド番号が指定されていません。|  
|`usRevisionNumber`|参照アセンブリのリビジョン番号。 この値は、0 にすることはできません。 場合のすべてのビット`usRevisionNumber`は設定されて、リビジョン番号が指定されていません。|  
|`szLocale`|参照先アセンブリによってサポートされるロケールを指定する、セミコロンで区切られた、RFC1766 仕様に準拠しているロケール名の一覧。 Null 値には、ロケールに依存しないことを示します。 **注:**.NET framework バージョン 1.0 は、複数のロケールを指定することはできません。|  
|`cbLocale`|ワイド文字単位サイズ`szLocale`します。|  
|`rdwProcessor`|参照アセンブリでサポートされているプロセッサの種類について、Winnt.h で定義されている、識別子の配列。 NULL 値では、プロセッサの独立性を示します。|  
|`ulProcessor`|長さ、`rdwProcessor`配列。|  
|`rOS`|配列の[OSINFO](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)参照アセンブリでサポートされているオペレーティング システムを指定するインスタンス。 NULL 値には、オペレーティング システムに依存しないことを示します。|  
|`ulOS`|長さ、`rOS`配列。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO 構造体](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
