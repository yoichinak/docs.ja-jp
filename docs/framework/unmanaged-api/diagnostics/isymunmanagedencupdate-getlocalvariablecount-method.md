---
title: ISymUnmanagedENCUpdate::GetLocalVariableCount メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate.GetLocalVariableCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount
helpviewer_keywords:
- ISymUnmanagedENCUpdate::GetLocalVariableCount method [.NET Framework debugging]
- GetLocalVariableCount method [.NET Framework debugging]
ms.assetid: 9777d8bb-4abc-4be8-aa7c-34f853eceb9c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a8a56d9655a2754c110c08517229a39011d82c5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482458"
---
# <a name="isymunmanagedencupdategetlocalvariablecount-method"></a>ISymUnmanagedENCUpdate::GetLocalVariableCount メソッド
ローカル変数の数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetLocalVariableCount(  
    [in]  mdMethodDef  mdMethodToken,  
    [out] ULONG        *pcLocals);  
```  
  
## <a name="parameters"></a>パラメーター  
 `mdMethodToken`  
 [in]メソッドのメタデータ トークン。  
  
 `pcLocals`  
 [out]ポインター、`ULONG32`ローカル変数の数を格納するために必要なバッファーの文字のサイズを受け取る。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目
- [ISymUnmanagedENCUpdate インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)
