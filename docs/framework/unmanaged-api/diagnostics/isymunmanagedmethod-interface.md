---
title: ISymUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c29656a4787c674886505a3be2508470460dfc10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939530"
---
# <a name="isymunmanagedmethod-interface"></a>ISymUnmanagedMethod インターフェイス
シンボル ストア内のメソッドを表します。 このインターフェイスは、型に関連する属性ではなく、メソッドのシンボルに関連する属性のみへのアクセスを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|このメソッドを定義する名前空間を取得します。|  
|[GetOffset メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|ドキュメント内の位置を指定するには、対応するこのメソッド内のオフセットを返します。|  
|[GetParameters メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|このメソッドのパラメーターを取得します。|  
|[GetRanges メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|指定されたドキュメント内の位置には、Microsoft intermediate language (MSIL をこのメソッド内の位置に含まれる) の範囲に先頭と末尾オフセットのペアの対応する配列を返します。|  
|[GetRootScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|このメソッド内でルート構文スコープを取得します。 このスコープはメソッド全体を囲みます。|  
|[GetScopeFromOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|このメソッドを指定したオフセットを囲む内で最も外側の構文のスコープを取得します。|  
|[GetSequencePointCount メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|このメソッド内のシーケンス ポイントの数を取得します。|  
|[GetSequencePoints メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|このメソッド内のすべてのシーケンス ポイントを取得します。|  
|[GetSourceStartEnd メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|このメソッドのソースの先頭と末尾のドキュメントの位置を取得します。|  
|[GetToken メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|このメソッドのメタデータ トークンを返します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
