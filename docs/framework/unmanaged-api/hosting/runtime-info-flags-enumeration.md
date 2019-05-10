---
title: RUNTIME_INFO_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0f4b6e024d75d9334f91373f9d3bbd2c5e41093
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64622512"
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS 列挙型
共通言語ランタイム (CLR) に関する情報を返す必要があるかを示す値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|ディレクトリ情報を含める必要があることを示します。|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|バージョン情報を含める必要があることを示します。|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|障害発生時にエラー ダイアログ ボックスを表示しないことを示します。|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|示します呼び出し元の効果、 [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS フラグを使用して関数をオーバーライドする必要があります。 つまり、抑制されるのではなく、障害発生時にインストールのダイアログ ボックスを表示する必要があります。|  
|`RUNTIME_INFO_REQUEST_AMD64`|については、AMD 64 互換性のあるバージョンのランタイムの要求を示します。|  
|`RUNTIME_INFO_REQUEST_IA64`|IA 64 互換性のあるランタイムのバージョンに関する情報の要求を示します。|  
|`RUNTIME_INFO_REQUEST_X86`|X86 と互換性のあるランタイムのバージョンに関する情報の要求を示します。|  
|`RUNTIME_INFO_UPGRADE_VERSION`|バージョンのアップグレードについてを含める必要があることを示します。|  
  
## <a name="remarks"></a>Remarks  
 次のプラットフォーム アーキテクチャ フラグは、一度に 1 つのみ指定でき、組み合わせることはできません。  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
