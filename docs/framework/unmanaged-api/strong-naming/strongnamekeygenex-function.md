---
title: StrongNameKeyGenEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameKeyGenEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameKeyGenEx
helpviewer_keywords:
- StrongNameKeyGenEx function [.NET Framework strong naming]
ms.assetid: 36bd10b9-9857-45f3-8d3b-0da091d6169e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9ab908866402bd7a883114466f32921321a5ee6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799011"
---
# <a name="strongnamekeygenex-function"></a>StrongNameKeyGenEx 関数
厳密な名前の使用のために、指定されたキーサイズを持つ新しい公開/秘密キーのペアを生成します。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameKeyGenEx](../hosting/iclrstrongname-strongnamekeygenex-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameKeyGenEx (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [in]  DWORD     dwKeySize,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszKeyContainer`  
 から要求されたキーコンテナー名。 `wszKeyContainer`は空でない文字列である必要があります。または、一時名を生成する場合は null にする必要があります。  
  
 `dwFlags`  
 からキーを登録したままにするかどうかを指定します。 次の値がサポートされています。  
  
- 0x00000000-が null `wszKeyContainer`の場合に、一時キーコンテナー名を生成するために使用されます。  
  
- 0x00000001 (`SN_LEAVE_KEY`)-キーを登録したままにすることを指定します。  
  
 `dwKeySize`  
 から要求されたキーのサイズ (ビット単位)。  
  
 `ppbKeyBlob`  
 入出力返された公開/秘密キーのペア。  
  
 `pcbKeyBlob`  
 入出力の`ppbKeyBlob`サイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に完了した場合は。それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 .NET Framework バージョン1.0 および1.1 では、 `dwKeySize`厳密な名前でアセンブリに署名するには1024ビットが必要です。バージョン2.0 では、2048ビットキーのサポートが追加されます。  
  
 キーが取得されたら、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md)関数を呼び出して、割り当てられたメモリを解放する必要があります。  
  
 関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameKeyGenEx`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameKeyGenEx メソッド](../hosting/iclrstrongname-strongnamekeygenex-method.md)
- [StrongNameKeyGen メソッド](../hosting/iclrstrongname-strongnamekeygen-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
