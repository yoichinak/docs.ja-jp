---
title: ICorProfilerCallback::Shutdown メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041757"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown メソッド
アプリケーションのシャット ダウンをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Remarks  
 プロファイラー コードがのメソッドを安全に呼び出すことはできません、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)インターフェイスの後に、`Shutdown`メソッドが呼び出されます。 呼び出し`ICorProfilerInfo`メソッドの後に未定義の動作が発生する、`Shutdown`メソッドを返します。 シャット ダウン後に特定の変更できないイベントが発生します。プロファイラーは、これが発生したときにすぐに返される注意する必要があります。  
  
 `Shutdown`プロファイリングされているマネージ アプリケーションがマネージ コードとして起動する場合にのみ、メソッドが呼び出されます (つまり、プロセスのスタックの最初のフレームが管理対象)。 アプリケーションがアンマネージ コードとして開始された後でマネージ コードにジャンプする場合は、それによってインスタンスを作成する共通言語ランタイム (CLR) の`Shutdown`は呼び出されません。 ような場合、プロファイラーは、ライブラリに含める必要があります、 `DllMain` DLL_PROCESS_DETACH を使用するルーチンの値をすべてのリソースを解放し、これにディスクにトレースのフラッシュなどのデータのクリーンアップ処理を実行します。  
  
 一般に、プロファイラーは、予期しないシャット ダウンに対処する必要があります。 たとえば、win32 のプロセスを中止する可能性があります`TerminateProcess`メソッド (Winbase.h で宣言)。 それ以外の場合、CLR は、それらの計画的な破棄のメッセージを配信することがなく、特定のマネージ スレッド (バック グラウンド スレッド) を停止します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
