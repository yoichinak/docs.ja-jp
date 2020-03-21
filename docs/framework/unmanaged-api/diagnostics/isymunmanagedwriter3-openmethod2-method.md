---
title: ISymUnmanagedWriter3::OpenMethod2 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3.OpenMethod2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3::OpenMethod2
helpviewer_keywords:
- ISymUnmanagedWriter3::OpenMethod2 method [.NET Framework debugging]
- OpenMethod2 method [.NET Framework debugging]
ms.assetid: 025e358c-448f-4423-a2f2-57acf437c8a5
topic_type:
- apiref
ms.openlocfilehash: 0c112819ef3bc4f9a7146ee80f55202ff89d689a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178314"
---
# <a name="isymunmanagedwriter3openmethod2-method"></a>ISymUnmanagedWriter3::OpenMethod2 メソッド
メソッドを開き、イメージ内の実際のセクション オフセットを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT OpenMethod2(
    [in] mdMethodDef method,  
    [in] ULONG32 isect,  
    [in] ULONG32 offset);  
```  
  
## <a name="parameters"></a>パラメーター  
 `method`  
 [in]開くメソッドのメタデータ トークン。  
  
 `isect`  
 [in]イメージ内のセクション オフセット。  
  
 `offset`  
 [in]イメージ内のオフセット。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合はS_OK。それ以外の場合は、E_FAILまたはその他のエラー コードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** コーシム.idl,コーシム.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter3 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
- [OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)
