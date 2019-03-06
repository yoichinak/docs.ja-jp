---
title: ICorDebug::CreateProcess メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CreateProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CreateProcess
helpviewer_keywords:
- ICorDebug::CreateProcess method [.NET Framework debugging]
- CreateProcess method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: b6128694-11ed-46e7-bd4e-49ea1914c46a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf7480eaa0fa38651d139a2fa9d533b43dbdce1b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496470"
---
# <a name="icordebugcreateprocess-method"></a>ICorDebug::CreateProcess メソッド
プロセスと、デバッガーの制御下で、プライマリ スレッドを起動します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateProcess (  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess            **ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `lpApplicationName`  
 [in]実行中のプロセスによって実行されるモジュールを指定する null で終わる文字列へのポインター。 モジュールは、呼び出し元のプロセスのセキュリティ コンテキストで実行されます。  
  
 `lpCommandLine`  
 [in]実行中のプロセスによって実行されるコマンドラインを指定する null で終わる文字列へのポインター。 アプリケーション名 (たとえば、"SomeApp.exe") は、最初の引数である必要があります。  
  
 `lpProcessAttributes`  
 [in]Win32 へのポインター`SECURITY_ATTRIBUTES`プロセスのセキュリティ記述子を指定する構造体。 場合`lpProcessAttributes`が null の場合、既定のセキュリティ記述子は、プロセスに取得します。  
  
 `lpThreadAttributes`  
 [in]Win32 へのポインター`SECURITY_ATTRIBUTES`プロセスのプライマリ スレッドのセキュリティ記述子を指定する構造体。 場合`lpThreadAttributes`が null の場合、既定のセキュリティ記述子は、スレッドに取得します。  
  
 `bInheritHandles`  
 [in]設定`true`、実行中のプロセスによって呼び出し元のプロセスで継承可能な各ハンドルを継承することを示すまたは`false`ハンドルを継承しないことを示します。 継承されたハンドルは、元のハンドルと同じ値とアクセス権限を持っています。  
  
 `dwCreationFlags`  
 [in]ビットごとの組み合わせ、 [Win32 プロセス作成フラグ](https://go.microsoft.com/fwlink/?linkid=69981)優先度クラスと、実行中のプロセスの動作を制御します。  
  
 `lpEnvironment`  
 [in]新しいプロセスの環境ブロックへのポインター。  
  
 `lpCurrentDirectory`  
 [in]プロセスの現在のディレクトリにフルパスを指定する null で終わる文字列へのポインター。 このパラメーターが null の場合、新しいプロセスは、呼び出し元プロセスとして同じの現在のドライブとディレクトリがあります。  
  
 `lpStartupInfo`  
 [in]Win32 へのポインター`STARTUPINFOW`ウィンドウ ステーション、デスクトップ、標準のハンドル、および実行中のプロセスのメイン ウィンドウの外観を指定する構造体。  
  
 `lpProcessInformation`  
 [in]Win32 へのポインター`PROCESS_INFORMATION`を起動するプロセスに関する識別情報を指定します。  
  
 `debuggingFlags`  
 [in]デバッグ オプションを指定する CorDebugCreateProcessFlags 列挙型の値。  
  
 `ppProcess`  
 [out]プロセスを表す ICorDebugProcess オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 このメソッドのパラメーターは、Win32 のと同じ`CreateProcess`メソッド。  
  
 アンマネージの混在モードのデバッグを有効にするには設定`dwCreationFlags`DEBUG_PROCESS に&#124;DEBUG_ONLY_THIS_PROCESS します。 マネージ デバッグのみを使用する場合は、これらのフラグを設定しないでください。  
  
 かどうか、デバッガーとプロセスをデバッグ (アタッチされたプロセス)、単一のコンソールを共有し、相互運用機能デバッグを使用する場合は、コンソールのロックを保持して、デバッグ イベントで停止にアタッチされたプロセスのことです。 デバッガーにし、コンソールを使用しようがブロックされます。 この問題を回避するで防ぐを設定、`dwCreationFlags`パラメーター。  
  
 IA 64 ベースおよび AMD64 ベースのプラットフォームなどの Win9x と x86 以外のプラットフォームでは、相互運用機能デバッグはサポートされていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
