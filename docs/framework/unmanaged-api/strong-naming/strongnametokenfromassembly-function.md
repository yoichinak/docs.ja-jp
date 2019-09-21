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
ms.openlocfilehash: 71058a1ff82335b2a341904805d06738e662c296
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798861"
---
# <a name="strongnametokenfromassembly-function"></a>StrongNameTokenFromAssembly 関数
指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameTokenFromAssembly](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameTokenFromAssembly (  
    [in]  LPCWSTR   wszFilePath,  
    [out] BYTE      **ppbStrongNameToken,  
    [out] ULONG     *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 からアセンブリのポータブル実行可能 (PE) ファイルへのパス。  
  
 `ppbStrongNameToken`  
 入出力返された厳密な名前トークン。  
  
 `pcbStrongNameToken`  
 入出力厳密な名前トークンのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に完了した場合は。それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 厳密な名前トークンは、公開キーの短縮形です。 トークンは、アセンブリの署名に使用される公開キーから作成された64ビットのハッシュです。 トークンはアセンブリの厳密な名前の一部であり、アセンブリメタデータから読み取ることができます。  
  
 トークンが作成されたら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md)関数を呼び出して、割り当てられたメモリを解放する必要があります。  
  
 関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameTokenFromAssembly`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromAssembly メソッド](../hosting/iclrstrongname-strongnametokenfromassembly-method.md)
- [StrongNameTokenFromAssemblyEx メソッド](../hosting/iclrstrongname-strongnametokenfromassemblyex-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
