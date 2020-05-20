---
title: シンボル ストア診断インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
ms.openlocfilehash: 044ed5e08a85442c5a73c123cf51529d2fd3f1fc
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442177"
---
# <a name="diagnostics-symbol-store-interfaces"></a>シンボル ストア診断インターフェイス
このトピックでは、コンパイラがデバッガーで使用するシンボル情報を生成できるようにするアンマネージインターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IBindingDisplay インターフェイス](ibindingdisplay-interface.md)  
 実行中のアプリケーションに関する現在のバインド情報を表示するメソッドを提供します。  
  
 [IDebugAutoAttach インターフェイス](idebugautoattach-interface.md)  
 サーバーによって呼び出されるデバッガーの自動アタッチのインターフェイスを定義します。  
  
 [INotifyConnection2 インターフェイス](inotifyconnection2-interface.md)  
 接続通知ソースを登録および登録解除するためのメソッドを宣言します。  
  
 [INotifySink2 インターフェイス](inotifysink2-interface.md)  
 シンク通知のメソッドを宣言します。  
  
 [INotifySource2 インターフェイス](inotifysource2-interface.md)  
 通知フィルターを設定するためのメソッドを宣言します。  
  
 [ISymENCUnmanagedMethod インターフェイス](isymencunmanagedmethod-interface.md)  
 エディットコンティニュ機能に関する情報を提供します。  
  
 [ISymUnmanagedAsyncMethod インターフェイス](isymunmanagedasyncmethod-interface.md)  
 このインターフェイスは、 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)への読み取り補数です。  
  
 [ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](isymunmanagedasyncmethodpropertieswriter-interface.md)  
 メソッドシンボルごとにオプションの非同期メソッド情報を定義できます。 は、開いているメソッド (つまり、 [Openmethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)と[closemethod メソッド](isymunmanagedwriter-closemethod-method.md)の呼び出しの間) でを使用する必要があります。  
  
 [ISymUnmanagedBinder インターフェイス](isymunmanagedbinder-interface.md)  
 アンマネージコードのシンボルバインダーを表します。  
  
 [ISymUnmanagedBinder2 インターフェイス](isymunmanagedbinder2-interface.md)  
 アンマネージコードのシンボルバインダーを表し、インターフェイスを拡張し `ISymUnmanagedBinder` ます。  
  
 [ISymUnmanagedBinder3 インターフェイス](isymunmanagedbinder3-interface.md)  
 アンマネージコードのシンボルバインダーを表し、インターフェイスを拡張し `ISymUnmanagedBinder` ます。  
  
 [ISymUnmanagedConstant インターフェイス](isymunmanagedconstant-interface.md)  
 アンマネージ定数へのアクセスを提供します。  
  
 [ISymUnmanagedDispose インターフェイス](isymunmanageddispose-interface.md)  
 アンマネージリソースを破棄します。  
  
 [ISymUnmanagedDocument インターフェイス](isymunmanageddocument-interface.md)  
 シンボル ストアによって参照されるドキュメントを表します。  
  
 [ISymUnmanagedDocumentWriter インターフェイス](isymunmanageddocumentwriter-interface.md)  
 シンボル ストアで参照されるドキュメントに書き込むためのメソッドを提供します。  
  
 [ISymUnmanagedENCUpdate インターフェイス](isymunmanagedencupdate-interface.md)  
 エディットコンティニュ機能のメソッドを提供します。  
  
 [ISymUnmanagedMethod インターフェイス](isymunmanagedmethod-interface.md)  
 シンボルストア内のメソッドを表します。  
  
 [ISymUnmanagedNamespace インターフェイス](isymunmanagednamespace-interface.md)  
 名前空間を表します。  
  
 [ISymUnmanagedReader インターフェイス](isymunmanagedreader-interface.md)  
 シンボルストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボルリーダーを表します。  
  
 [ISymUnmanagedReader2 インターフェイス](isymunmanagedreader2-interface.md)  
 メソッドトークンと編集およびコピーバージョン番号を指定して、シンボルリーダーメソッドを取得します。  
  
 [ISymUnmanagedReaderSymbolSearchInfo インターフェイス](isymunmanagedreadersymbolsearchinfo-interface.md)  
 シンボル検索情報を取得するメソッドを提供します。  
  
 [ISymUnmanagedScope インターフェイス](isymunmanagedscope-interface.md)  
 メソッド内の構文のスコープを表します。  
  
 [ISymUnmanagedScope2 インターフェイス](isymunmanagedscope2-interface.md)  
 メソッド内の構文のスコープを表し、 `ISymUnmanagedScope` スコープ内で定義された定数に関する情報を取得するメソッドを使用してインターフェイスを拡張します。「」を参照してください。  
  
 [ISymUnmanagedSourceServerModule インターフェイス](isymunmanagedsourceservermodule-interface.md)  
 モジュールのソースサーバーデータを提供します。  
  
 [ISymUnmanagedSymbolSearchInfo インターフェイス](isymunmanagedsymbolsearchinfo-interface.md)  
 検索パスに関する情報を取得するメソッドを提供します。  
  
 [ISymUnmanagedVariable インターフェイス](isymunmanagedvariable-interface.md)  
 パラメーター、ローカル変数、フィールドなどの変数を表します。  
  
 [ISymUnmanagedWriter インターフェイス](isymunmanagedwriter-interface.md)  
 シンボルライターを表し、ドキュメント、シーケンスポイント、構文スコープ、および変数を定義するメソッドを提供します。  
  
 [ISymUnmanagedWriter2 インターフェイス](isymunmanagedwriter2-interface.md)  
 シンボルライターを表し、ドキュメント、シーケンスポイント、構文スコープ、および変数を定義するメソッドを提供します。 インターフェイスを拡張 `ISymUnmanagedWriter` します。  
  
 [ISymUnmanagedWriter3 インターフェイス](isymunmanagedwriter3-interface.md)  
 シンボルライターを表し、ドキュメント、シーケンスポイント、構文スコープ、および変数を定義するメソッドを提供します。 インターフェイスを拡張 `ISymUnmanagedWriter` します。  
  
 [ISymUnmanagedWriter4 インターフェイス](isymunmanagedwriter4-interface.md)  
 ISymUnmanagedWriter4 インターフェイス。  
  
 [ISymUnmanagedWriter5 インターフェイス](isymunmanagedwriter5-interface.md)  
 ISymUnmanagedWriter5 インターフェイス。  
  
## <a name="related-sections"></a>関連項目  
 [シンボル ストア診断列挙型](diagnostics-symbol-store-enumerations.md)  
  
 [シンボル ストア診断構造体](diagnostics-symbol-store-structures.md)  
  
 [デバッグ](../debugging/index.md)
