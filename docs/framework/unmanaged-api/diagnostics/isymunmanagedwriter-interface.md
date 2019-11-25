---
title: ISymUnmanagedWriter インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: fc19ee25e903046daef376e4297c8feb3d01ad47
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427937"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter インターフェイス
Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|Closes the symbol writer without committing the symbols to the symbol store.|  
|[Close メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|Closes the symbol writer after committing the symbols to the symbol store.|  
|[CloseMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|現在のメソッドを閉じます。 Once a method is closed, no more symbols can be defined within it.|  
|[CloseNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|Closes the most recently opened namespace.|  
|[CloseScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|現在の構文のスコープを閉じます。|  
|[DefineConstant メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|Defines a name for a constant value.|  
|[DefineDocument メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|ソース ドキュメントを定義します。|  
|[DefineField メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|Defines a single variable that is not within a method.|  
|[DefineGlobalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|Defines a single global variable.|  
|[DefineLocalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|現在の構文のスコープの変数を 1 つ定義します。|  
|[DefineParameter メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|Defines a single parameter in the current method.|  
|[DefineSequencePoints メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|現在のメソッド内のシーケンス ポイントのグループを定義します。|  
|[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.|  
|[Initialize2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|Sets the metadata emitter interface with which this writer will be associated, sets the output file name to which the debugging symbols will be written, and sets the final location of the program database (PDB) file.|  
|[OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|Opens a method into which symbol information is emitted.|  
|[OpenNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|新しい名前空間を開きます。|  
|[OpenScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|現在のメソッドの構文の新しいスコープを開きます。|  
|[RemapToken メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.|  
|[SetMethodSourceRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|Specifies the true start and end of a method within a source file.|  
|[SetScopeRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|指定した構文のスコープのオフセット範囲を定義します。|  
|[SetSymAttribute メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|Defines a custom attribute based upon its name.|  
|[SetUserEntryPoint メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|Specifies the user-defined method that is the entry point for this module.|  
|[UsingNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.|  
  
## <a name="requirements"></a>［要件］  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
