---
title: StrongNameTokenFromAssembly 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromAssembly
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameTokenFromAssembly
helpviewer_keywords:
- StrongNameTokenFromAssembly function [.NET Framework strong naming]
ms.assetid: 0a4b47ee-02f6-4a98-864e-a6f11ca3f2d9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46d8013d43dc14807804502e4a0820a2928f917e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499239"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly 関数
指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnametokenfromassembly](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]アセンブリのポータブル実行可能 (PE) ファイルへのパス。  
  
 `ppbStrongNameToken`  
 [out]厳密な名前が返されたトークンです。  
  
 `pcbStrongNameToken`  
 [out]厳密な名前トークンのバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 厳密な名前トークンは、公開キーの短縮形です。 トークンは、アセンブリの署名に使用する公開キーから作成される 64 ビット ハッシュです。 トークンは、アセンブリの厳密な名前の一部であるし、アセンブリのメタデータから読み取ることができます。  
  
 呼び出す必要があります、トークンが作成された後、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)割り当てられたメモリを解放する関数。  
  
 場合、`StrongNameTokenFromAssembly`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** Mscoree.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [StrongNameTokenFromAssembly メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
