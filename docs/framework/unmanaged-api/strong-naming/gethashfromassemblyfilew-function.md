---
title: GetHashFromAssemblyFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromAssemblyFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromAssemblyFileW
helpviewer_keywords:
- GetHashFromAssemblyFileW function [.NET Framework strong naming]
ms.assetid: d1b2b172-5353-42af-a877-cf653c68ece0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4b748370ff1aff042923002ad827a0e39d99963
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799273"
---
# <a name="gethashfromassemblyfilew-function"></a>GetHashFromAssemblyFileW 関数
指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。 アセンブリファイルへのパスは、Unicode 文字列として指定する必要があります。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: GetHashFromAssemblyFileW](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromAssemblyFileW (  
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 からハッシュされるファイルへのパス。 このパラメーターは Unicode 文字列である必要があります。  
  
 `piHashAlg`  
 [入力、出力]ハッシュアルゴリズムを指定する定数。 既定のハッシュアルゴリズムには0を使用します。  
  
 `pbHash`  
 入出力返されたハッシュバッファー。  
  
 `cchHash`  
 から要求された最大`pbHash`サイズ。  
  
 `pchHash`  
 入出力の`pbHash`返されたサイズ (バイト単位)。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromAssemblyFileW メソッド](../hosting/iclrstrongname-gethashfromassemblyfilew-method.md)
- [GetHashFromAssemblyFile メソッド](../hosting/iclrstrongname-gethashfromassemblyfile-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
