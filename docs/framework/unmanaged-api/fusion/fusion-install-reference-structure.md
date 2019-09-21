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
ms.openlocfilehash: 9e81fb7c99b9fd03a69456a84f2191770f40121d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795349"
---
# <a name="fusion_install_reference-structure"></a>FUSION_INSTALL_REFERENCE 構造体
アプリケーションがグローバルアセンブリキャッシュにインストールしたアセンブリに対して行う参照を表します。  
  
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
|`cbSize`|構造体のサイズ (バイト単位)。|  
|`dwFlags`|将来の拡張のために予約されています。 この値は 0 (ゼロ) にする必要があります。|  
|`guidScheme`|参照を追加するエンティティ。 このフィールドには、次のいずれかの値を指定できます。<br /><br /> - FUSION_REFCOUNT_MSI_GUID:アセンブリは、Microsoft Windows インストーラーを使用してインストールされたアプリケーションによって参照されます。 フィールドはに`MSI`設定され、`Windows Installer`フィールドはに設定されます。 `szNonCanonicalData` `szIdentifier` このスキームは、Windows サイドバイサイドアセンブリに使用されます。<br />- FUSION_REFCOUNT_UNINSTALL_SUBKEY_GUID:アセンブリは、 **[プログラムの追加と削除]** インターフェイスに表示されるアプリケーションによって参照されます。 フィールド`szIdentifier`は、アプリケーションを **[プログラムの追加と削除]** インターフェイスに登録するトークンを提供します。<br />- FUSION_REFCOUNT_FILEPATH_GUID:アセンブリは、ファイルシステム内のファイルによって表されるアプリケーションによって参照されます。 `szIdentifier`フィールドには、このファイルへのパスが表示されます。<br />- FUSION_REFCOUNT_OPAQUE_STRING_GUID:アセンブリは、不透明な文字列によってのみ表されるアプリケーションによって参照されています。 フィールド`szIdentifier`は、この不透明な文字列を提供します。 グローバルアセンブリキャッシュは、この値を削除するときに、不透明な参照が存在するかどうかを確認しません。<br />- FUSION_REFCOUNT_OSINSTALL_GUID:この値は予約されています。|  
|`szIdentifier`|グローバルアセンブリキャッシュにアセンブリをインストールしたアプリケーションを識別する一意の文字列。 値は、 `guidScheme`フィールドの値によって異なります。|  
|`szNonCanonicalData`|参照を追加するエンティティによってのみ認識される文字列。 グローバルアセンブリキャッシュはこの文字列を格納しますが、この文字列は使用しません。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion 構造体](fusion-structures.md)
- [グローバル アセンブリ キャッシュ](../../app-domains/gac.md)
