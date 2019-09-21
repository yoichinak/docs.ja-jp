---
title: GetHashFromFileW 関数
ms.date: 03/30/2017
api_name:
- GetHashFromFileW
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFileW
helpviewer_keywords:
- GetHashFromFileW function [.NET Framework strong naming]
ms.assetid: 97c2d7a6-5376-45a1-ba65-146a249147cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fd96b5acb22f63b6e06c981119186680d6593a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799188"
---
# <a name="gethashfromfilew-function"></a>GetHashFromFileW 関数
Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: GetHashFromFileW](../hosting/iclrstrongname-gethashfromfilew-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromFileW (   
    [in]  LPCWSTR   wszFilePath,  
    [in, out] unsigned int   *piHashAlg,  
    [out] BYTE      *pbHash,  
    [in]  DWORD     cchHash,  
    [out] DWORD     *pchHash  
);   
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 からハッシュするファイルの Unicode 名。  
  
 `piHashAlg`  
 [入力、出力]ハッシュを生成するときに使用するアルゴリズム。 有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。 が`piHashAlg` 0 に設定されている場合は、既定のアルゴリズム CALG_SHA が使用されます。  
  
 `pbHash`  
 入出力生成されたハッシュを格納しているバイト配列。  
  
 `cchHash`  
 からが指す`pbHash`バッファーの最大サイズ。  
  
 `pchHash`  
 入出力の`pbHash`サイズ (バイト単位)。  
  
## <a name="remarks"></a>Remarks  
 この関数は[GetHashFromFile](gethashfromfile-function.md)と同じですが、ファイル名の指定は ANSI ではなく Unicode である点が異なります。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromFileW メソッド](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [GetHashFromFile メソッド](../hosting/iclrstrongname-gethashfromfile-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
