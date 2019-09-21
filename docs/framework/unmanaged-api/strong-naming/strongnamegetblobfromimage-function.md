---
title: StrongNameGetBlobFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage function [.NET Framework strong naming]
ms.assetid: 1de658e6-da32-4d01-9097-6f43c92222e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86b99b29a85f498a6bfa0363a446bf589876bff9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799091"
---
# <a name="strongnamegetblobfromimage-function"></a>StrongNameGetBlobFromImage 関数
指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameGetBlobFromImage](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbBase`  
 からマップされたアセンブリマニフェストのメモリアドレス。  
  
 `dwLength`  
 からにある`pbBase`イメージのサイズ (バイト単位)。  
  
 `pbBlob`  
 からイメージのバイナリ表現を格納するバッファー。  
  
 `pcbBlob`  
 [入力、出力]要求された最大サイズ (バイト`pbBlob`単位)。 戻り時に、の実際の`pbBlob`サイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に完了した場合は。それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameGetBlobFromImage`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetBlobFromImage メソッド](../hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [StrongNameGetBlob メソッド](../hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
