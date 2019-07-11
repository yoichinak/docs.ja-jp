---
title: FUSION_INSTALL_REFERENCE 構造体
ms.date: 03/30/2017
api_name:
- FUSION_INSTALL_REFERENCE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- FUSION_INSTALL_REFERENCE
helpviewer_keywords:
- FUSION_INSTALL_REFERENCE structure [.NET Framework fusion]
ms.assetid: ae181ec8-36bf-4ed1-9a02-ca27d417c80b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec18d5d5a6574cb0e08a6c4d6eaedcbcbf6886cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759364"
---
# <a name="fusioninstallreference-structure"></a>FUSION_INSTALL_REFERENCE 構造体
アプリケーションがグローバル アセンブリ キャッシュにアプリケーションがインストールされているアセンブリに参照を表します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _FUSION_INSTALL_REFERENCE_ {  
    DWORD    cbSize,  
    DWORD    dwFlags,  
    GUID     guidScheme,  
    LPCWSTR  szIdentifier,  
    LPCWSTR  szNonCanonicalData  
} FUSION_INSTALL_REFERENCE, *LPFUSION_INSTALL_REFERENCE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`cbSize`|(バイト単位) 構造体のサイズ。|  
|`dwFlags`|将来の機能拡張予約されています。 この値は 0 (ゼロ) である必要があります。|  
|`guidScheme`|このエンティティの参照を追加します。 このフィールドは、次の値のいずれかを指定できます。<br /><br /> -FUSION_REFCOUNT_MSI_GUID:アセンブリは、Microsoft Windows インストーラーを使用してインストールされたアプリケーションで参照されます。 `szIdentifier`にフィールドが設定されている`MSI`、および`szNonCanonicalData`にフィールドが設定されている`Windows Installer`します。 このスキームは、Windows のサイド バイ サイド アセンブリに使用されます。<br />-FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID:アセンブリが含まれているアプリケーションによって参照される、**プログラムの追加/削除**インターフェイス。 `szIdentifier`フィールドを使用してアプリケーションを登録するトークンを提供する、**プログラムの追加/削除**インターフェイス。<br />-   FUSION_REFCOUNT_FILEPATH_GUID:アセンブリは、ファイル システム内のファイルで表されるアプリケーションで参照されます。 `szIdentifier`フィールドは、このファイルへのパスを提供します。<br />-   FUSION_REFCOUNT_OPAQUE_STRING_GUID:アセンブリは、不透明な文字列のみで表されるアプリケーションで参照されます。 `szIdentifier`フィールドは、この不透明な文字列を提供します。 この値を削除すると、グローバル アセンブリ キャッシュはあいまいな参照の存在チェックをしません。<br />-   FUSION_REFCOUNT_OSINSTALL_GUID:この値は予約されています。|  
|`szIdentifier`|アセンブリをグローバル アセンブリ キャッシュにインストールされているアプリケーションを識別する一意の文字列。 その値の値によって異なります、`guidScheme`フィールド。|  
|`szNonCanonicalData`|参照を追加するエンティティのみが認識する文字列。 グローバル アセンブリ キャッシュでは、この文字列が格納されますが、使用しません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
- [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
