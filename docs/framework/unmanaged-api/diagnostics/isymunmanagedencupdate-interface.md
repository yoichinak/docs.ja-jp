---
title: ISymUnmanagedENCUpdate インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedENCUpdate
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedENCUpdate
helpviewer_keywords:
- ISymUnmanagedENCUpdate interface [.NET Framework debugging]
ms.assetid: 63a9ef45-01a6-46da-b958-5c6dc2dc232c
topic_type:
- apiref
ms.openlocfilehash: aa4fe2185ead7edfa47d4194799c930193e04076
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614527"
---
# <a name="isymunmanagedencupdate-interface"></a>ISymUnmanagedENCUpdate インターフェイス
エディットコンティニュ機能の関数を提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetLocalVariableCount メソッド](isymunmanagedencupdate-getlocalvariablecount-method.md)|ローカル変数の数を取得します。|  
|[GetLocalVariables メソッド](isymunmanagedencupdate-getlocalvariables-method.md)|ローカル変数を取得します。|  
|[InitializeForEnc メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-initializeforenc-method.md)|[ISymUnmanagedENCUpdate:: UpdateSymbolStore2](isymunmanagedencupdate-updatesymbolstore2-method.md)メソッドの最初の呼び出しの前にメソッドの境界を計算できるようにします。|  
|[UpdateMethodLines メソッド](isymunmanagedencupdate-updatemethodlines-method.md)|再コンパイルされていないが、行が個別に移動したメソッドの行情報を更新できるようにします。 各ステートメントのデルタが許可されます。|  
|[UpdateSymbolStore2 メソッド](isymunmanagedencupdate-updatesymbolstore2-method.md)|行情報が要件を満たしている場合に、コンパイラがプログラムデータベース (PDB) ストリームから変更されていない関数を省略できるようにします。 正しい行情報は、古い PDB 行情報と、関数内のすべての行に対して1つのデルタで判別できます。|  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym .idl、CorSym .h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](diagnostics-symbol-store-interfaces.md)
