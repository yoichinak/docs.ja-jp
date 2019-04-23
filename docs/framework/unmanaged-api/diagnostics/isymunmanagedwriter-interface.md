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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ac95cd5b79a2e1762fa9adf29d4d7926ab4ab7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150582"
---
# <a name="isymunmanagedwriter-interface"></a>ISymUnmanagedWriter インターフェイス
シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|シンボルをシンボル ストアにコミットせずには、シンボル ライターを閉じます。|  
|[Close メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|シンボルをシンボル ストアにコミットした後は、シンボル ライターを閉じます。|  
|[CloseMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|現在のメソッドを閉じます。 メソッドを終了すると、その中シンボルを定義できます。|  
|[CloseNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|終了は、最近名前空間を開きます。|  
|[CloseScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|現在の構文のスコープを閉じます。|  
|[DefineConstant メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|定数値の名前を定義します。|  
|[DefineDocument メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|ソース ドキュメントを定義します。|  
|[DefineField メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|メソッド内ではない 1 つの変数を定義します。|  
|[DefineGlobalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|1 つのグローバル変数を定義します。|  
|[DefineLocalVariable メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|現在の構文のスコープの変数を 1 つ定義します。|  
|[DefineParameter メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|現在のメソッドでは、1 つのパラメーターを定義します。|  
|[DefineSequencePoints メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|現在のメソッド内のシーケンス ポイントのグループを定義します。|  
|[GetDebugInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|コンパイラがポータブル実行可能 (PE) ファイル ヘッダーのデバッグ ディレクトリのエントリを書き込むために必要な情報を返します。|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。|  
|[Initialize2 メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|このライターが関連付けられるメタデータ エミッタ インターフェイスを設定、出力ファイル名をデバッグ シンボルが記述し、プログラム データベース (PDB) ファイルの最終的な場所の設定を設定します。|  
|[OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|シンボル情報の生成のメソッドを開きます。|  
|[OpenNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|新しい名前空間を開きます。|  
|[OpenScope メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|現在のメソッドの構文の新しいスコープを開きます。|  
|[RemapToken メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|メタデータ トークンが再マップされたメタデータの生成とするシンボルのライターに通知します。|  
|[SetMethodSourceRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|実際の先頭とソース ファイル内のメソッドの末尾を指定します。|  
|[SetScopeRange メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|指定した構文のスコープのオフセット範囲を定義します。|  
|[SetSymAttribute メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|その名前に基づくカスタム属性を定義します。|  
|[SetUserEntryPoint メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|このモジュールのエントリ ポイントは、ユーザー定義のメソッドを指定します。|  
|[UsingNamespace メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|指定した名前空間の完全修飾名が現在開いている構文のスコープ内で使用されているを指定します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
- [ISymUnmanagedWriter2 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)
- [ISymUnmanagedWriter3 インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
