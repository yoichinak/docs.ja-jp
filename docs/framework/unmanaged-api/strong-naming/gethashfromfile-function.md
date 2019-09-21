---
title: GetHashFromFile 関数
ms.date: 03/30/2017
api_name:
- GetHashFromFile
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromFile
helpviewer_keywords:
- GetHashFromFile function [.NET Framework strong naming]
ms.assetid: b3c526a4-8fb4-4ad6-b6af-42ce9c06492e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e79c1d89d767832022d487681e0515e5e92a7f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799219"
---
# <a name="gethashfromfile-function"></a>GetHashFromFile 関数
指定したファイルの内容に対してハッシュが生成されます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: GetHashFromFile](../hosting/iclrstrongname-gethashfromfile-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,   
    [out] BYTE     *pbHash,      
    [in]  DWORD    cchHash,      
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFilePath`  
 からハッシュするファイルの名前。  
  
 `piHashAlg`  
 [入力、出力]ハッシュを生成するときに使用するアルゴリズム。 有効なアルゴリズムは、Win32 CryptoAPI によって定義されているものです。 が`piHashAlg` 0 に設定されている場合は、既定のアルゴリズム CALG_SHA が使用されます。  
  
 `pbHash`  
 入出力生成されたハッシュを格納しているバイト配列。  
  
 `cchHash`  
 からが`pbHash`指すバッファーの最大サイズ。  
  
 `pchHash`  
 入出力返さ`pbHash`れたのサイズ (バイト単位)。  
  
## <a name="remarks"></a>Remarks  
 この関数は[GetHashFromFileW](gethashfromfilew-function.md)と同じですが、ファイル名の指定は Unicode ではなく ANSI である点が異なります。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromFile メソッド](../hosting/iclrstrongname-gethashfromfile-method.md)
- [GetHashFromFileW メソッド](../hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
