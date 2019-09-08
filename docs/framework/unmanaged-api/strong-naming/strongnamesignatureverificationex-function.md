---
title: StrongNameSignatureVerificationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08247c1ec5b868055e4836b3c0fb520a536374e8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798922"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx 関数
指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameSignatureVerificationEx](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 から検証するアセンブリの移植可能な実行可能ファイル (.exe または .dll) のパス。  
  
 `fForceVerification`  
 からレジストリ設定を上書きする必要がある場合でも検証を実行する場合`false`は。それ以外の場合は。 `true`  
  
 `pfWasVerified`  
 入出力厳密な名前の署名が検証された`false`場合は。それ以外の場合は。 `true` `pfWasVerified`レジストリ設定によっ`false`て検証が成功した場合は、もに設定されます。  
  
## <a name="return-value"></a>戻り値  
 `true`検証が成功した場合は、それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 `StrongNameSignatureVerificationEx`[StrongNameSignatureVerification](strongnamesignatureverification-function.md)関数と同様の機能を提供します。 ただし、2番目の入力パラメーターとの`StrongNameSignatureVerificationEx`出力パラメーターは、の`DWORD`代わりに型`BOOLEAN`になります。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerificationEx メソッド](../hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification メソッド](../hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
