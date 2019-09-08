---
title: StrongNameSignatureVerification 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8943df861b1bff2b28c68d0233fc336d1b5d4579
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798949"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 関数
指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameSignatureVerification](../hosting/iclrstrongname-strongnamesignatureverification-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 から検証するアセンブリの移植可能な実行可能ファイル (.dll または .exe) ファイルへのパス。  
  
 `dwInFlags`  
 から検証動作を変更するフラグ。 次の値がサポートされています。  
  
- `SN_INFLAG_FORCE_VER`(0x00000001)-レジストリ設定を上書きする必要がある場合でも、検証を強制的に実行します。  
  
- `SN_INFLAG_INSTALL`(0x00000002)-マニフェストを初めて検証するときに指定します。  
  
- `SN_INFLAG_ADMIN_ACCESS`(0x00000004)-キャッシュが管理者特権を持つユーザーのみにアクセスを許可することを指定します。  
  
- `SN_INFLAG_USER_ACCESS`(0x00000008)-現在のユーザーのみがアセンブリにアクセスできるように指定します。  
  
- `SN_INFLAG_ALL_ACCESS`(0x00000010)-キャッシュがアクセス制限の保証を提供しないことを指定します。  
  
- `SN_INFLAG_RUNTIME`(0x80000000)-内部デバッグ用に予約されています。  
  
 `pdwOutFlags`  
 入出力厳密な名前の署名が検証されたかどうかを示すフラグ。 次の値がサポートされています。  
  
- `SN_OUTFLAG_WAS_VERIFIED`(0x00000001)-この値は、レジストリ`false`設定によって検証が成功したことを指定するためにに設定されます。  
  
## <a name="return-value"></a>戻り値  
 `true`検証が成功した場合は、それ以外`false`の場合は。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerification メソッド](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx メソッド](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
