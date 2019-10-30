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
ms.openlocfilehash: 80643187045e7e96b9c18169c5e71287713d711f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106238"
---
# <a name="runtime_info_flags-enumeration"></a>RUNTIME_INFO_FLAGS 列挙型
共通言語ランタイム (CLR) に関する情報を返す必要があるかどうかを示す値を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|ディレクトリ情報を含めないことを示します。|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|バージョン情報を含めないことを示します。|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|エラーが発生したときにエラーダイアログボックスを表示しないことを示します。|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|SEM_FAILCRITICALERRORS フラグを使用して[SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242)関数を呼び出すことによる影響をオーバーライドする必要があることを示します。 つまり、エラーが発生すると、抑制されるのではなく、インストールのダイアログボックスが表示されます。|  
|`RUNTIME_INFO_REQUEST_AMD64`|AMD-64 互換バージョンのランタイムに関する情報の要求を示します。|  
|`RUNTIME_INFO_REQUEST_IA64`|IA-64 互換バージョンのランタイムに関する情報の要求を示します。|  
|`RUNTIME_INFO_REQUEST_X86`|ランタイムの x86 互換バージョンに関する情報の要求を示します。|  
|`RUNTIME_INFO_UPGRADE_VERSION`|バージョンのアップグレード情報を含める必要があることを示します。|  
  
## <a name="remarks"></a>Remarks  
 次のプラットフォームアーキテクチャフラグは一度に1つだけ指定でき、組み合わせることはできません。  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
