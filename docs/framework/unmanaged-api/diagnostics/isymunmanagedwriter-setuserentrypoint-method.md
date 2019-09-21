---
title: ISymUnmanagedWriter::SetUserEntryPoint メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetUserEntryPoint
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint
helpviewer_keywords:
- ISymUnmanagedWriter::SetUserEntryPoint method [.NET Framework debugging]
- SetUserEntryPoint method [.NET Framework debugging]
ms.assetid: d4dcc575-3ac8-4453-9be1-2b24f47363d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11dc050e2fe16a64db4ac95bb1386e2d90535e81
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895025"
---
# <a name="isymunmanagedwritersetuserentrypoint-method"></a>ISymUnmanagedWriter::SetUserEntryPoint メソッド
このモジュールのエントリポイントであるユーザー定義メソッドを指定します。 たとえば、このエントリポイントは、main の前にコンパイラで生成されたスタブではなく、ユーザーのメインメソッドである可能性があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetUserEntryPoint(  
    [in] mdMethodDef entryMethod);  
```  
  
## <a name="parameters"></a>パラメーター  
 `entryMethod`  
 からユーザーエントリポイントであるメソッドのメタデータトークン。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK を返します。それ以外の場合は E_FAIL またはその他のエラーコードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
