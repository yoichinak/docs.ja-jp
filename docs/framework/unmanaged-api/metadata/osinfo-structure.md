---
title: OSINFO 構造体
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175227"
---
# <a name="osinfo-structure"></a>OSINFO 構造体
アセンブリまたはモジュールのオペレーティング システムに関する詳細が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwOSPlatformId`|Windows プラットフォーム関数`GetVersionEx`で定義された識別子の値の 1 つ。 次の値がサポートされています。<br /><br /> - VER_PLATFORM_WIN32s、または 0x0000 を使用して、Windows 3.1 を指定します。<br />- VER_PLATFORM_WIN32_WINDOWS、または 0x0001 を使用して、Windows 95、Windows 98、またはオペレーティング システムを指定します。<br />- VER_PLATFORM_WIN32_NT、または 0x0002 を使用して、Windows NT またはそこから下位にインストールされたオペレーティング システムを指定します。|  
|`dwOSMajorVersion`|オペレーティング システムのメジャー バージョン、または任意のバージョンを示す NULL 値。|  
|`dwOSMinorVersion`|オペレーティング システムのマイナー バージョン、または任意のバージョンを示す NULL 値。|  
  
## <a name="remarks"></a>解説  
 `OSINFO`は、 Windows`OSVERSIONINFOEX`プラットフォーム関数`GetVersionEx`の呼び出しで使用される構造に基づいています。 この構造体は、オペレーティング システムのサポートを示すために ASSEMBLYMETADATA 構造体によって使用されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** コル・h  
  
 **ライブラリ:** MsCorEE.dll のリソースとして使用されます。  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
