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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775201"
---
# <a name="osinfo-structure"></a>OSINFO 構造体
アセンブリまたはモジュールのオペレーティング システムに関する詳細情報が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`dwOSPlatformId`|Microsoft Windows プラットフォームの関数で定義された識別子の値のいずれかの`GetVersionEx`します。 次の値がサポートされています。<br /><br /> -VER_PLATFORM_WIN32s、または 0x0000、Microsoft Windows 3.1 を指定します。<br />-VER_PLATFORM_WIN32_WINDOWS、または 0x0001、Windows 95、Windows 98、またはそれらの子孫のオペレーティング システムを指定します。<br />-VER_PLATFORM_WIN32_NT、または 0x0010、Windows NT またはそこから継承したオペレーティング システムを指定します。|  
|`dwOSMajorVersion`|オペレーティング システムのメジャー バージョン、または任意のバージョンを示す NULL 値。|  
|`dwOSMinorVersion`|オペレーティング システムのマイナー バージョン、または任意のバージョンを示す NULL 値。|  
  
## <a name="remarks"></a>Remarks  
 `OSINFO` に基づいて、`OSVERSIONINFOEX`構造体で使用される関数の呼び出しを Microsoft Windows プラットフォーム`GetVersionEx`します。 この構造体は、そのオペレーティング システムのサポートを示す ASSEMBLYMETADATA 構造体によって使用されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ構造体](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit インターフェイス](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
