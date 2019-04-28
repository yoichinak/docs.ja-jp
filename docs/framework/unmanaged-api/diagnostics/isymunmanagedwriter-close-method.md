---
title: ISymUnmanagedWriter::Close メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Close
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Close
helpviewer_keywords:
- Close method, ISymUnmanagedWriter interface [.NET Framework debugging]
- ISymUnmanagedWriter::Close method [.NET Framework debugging]
ms.assetid: 4cce59e1-80b9-4fc4-b3aa-126f1c5876bc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4d3497d3167715d3e8a04f10a6687260949e4a36
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934057"
---
# <a name="isymunmanagedwriterclose-method"></a>ISymUnmanagedWriter::Close メソッド
シンボルをシンボル ストアにコミットした後は、シンボル ライターを閉じます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Close();  
```  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は s_ok を返します。それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="remarks"></a>Remarks  
 この呼び出しの後、シンボルのライターが、以降の更新は無効になります。 シンボルをコミットせずシンボル ライターを閉じるには使用、 [isymunmanagedwriter::abort](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)メソッド代わりにします。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
