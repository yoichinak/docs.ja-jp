---
title: ExportTypeForwarder メソッド
ms.date: 03/30/2017
api_name:
- IALink.ExportTypeForwarder
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ExportTypeForwarder
helpviewer_keywords:
- ExportTypeForwarder method
ms.assetid: 55989fa9-ab43-4f08-8eb6-2eb56fa7ca76
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0ae4ddd07a2a3d3ab9b5d024eceb43329db96915
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787509"
---
# <a name="exporttypeforwarder-method"></a>ExportTypeForwarder メソッド
指定されたアセンブリの型テーブルに型フォワーダーを追加します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExportTypeForwarder(  
    mdAssemblyRef   tkAssemblyRef,  
    LPCWSTR         pszTypename,  
    DWORD           dwFlags,  
    mdExportedType* pType  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `tkAssemblyRef`  
 型フォワーダーが参照するアセンブリへの参照。  
  
 `pszTypename`  
 エクスポートする完全修飾型名。  
  
 `dwFlags`  
 `ComType``tdPublic` や`tdNested`などのフラグ。 この値は、この[メソッド](../metadata/imetadataassemblyemit-defineexportedtype-method.md)に渡すことができます。  
  
 `pType`  
 エクスポートされた型のトークンを受け取ります。 これは、入れ子にされた型を出力する場合にのみ必要です。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink. h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](ialink-interface.md)
- [IALink2 インターフェイス](ialink2-interface.md)
- [ALink API](index.md)
