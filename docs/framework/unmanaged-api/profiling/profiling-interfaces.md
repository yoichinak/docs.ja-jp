---
title: プロファイリングのインターフェイス
ms.date: 04/10/2018
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], profiling
- profiling interfaces [.NET Framework]
- interfaces [.NET Framework profiling]
ms.assetid: d9303db8-e881-4217-91b7-8c7573c8ef9e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 059fadc5607e76b871083682136fda542ae9bacf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758198"
---
# <a name="profiling-interfaces"></a>プロファイリングのインターフェイス
ここでは、共通言語ランタイム (CLR) で実行中のプログラムに対してプロファイルを可能にするアンマネージ インターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ICLRProfiling インターフェイス](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-interface.md)  
 提供、 [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)メソッドで、実行中のプロセスにアタッチするプロファイラーを使用します。  
  
 [ICorProfilerAssemblyReferenceProvider インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)  
 プロファイラーを追加するアセンブリ参照の CLR に通知できるように、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック。  
  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 プロファイラーがサブスクライブしたイベントが発生したときにコード プロファイラーに通知するために、CLR が使用するメソッドを提供します。  
  
 [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 .NET Framework 2.0 以降でサポートされるコールバックによって、`ICorProfilerCallback` インターフェイスを拡張します。  
  
 [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 CLR がプロファイラーにアタッチとデタッチの状態情報を伝えるために使用するコールバック メソッドを提供します。  
  
 [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 プロファイラーと情報をやりとりするために CLR が使用するコールバック メソッドを提供します。  
  
 [ICorProfilerCallback5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)  
 ガベージ コレクションのルートによって参照されるオブジェクトの遷移的なクロージャを識別するメソッドを提供します。  
  
 [ICorProfilerCallback6 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)  
 CLR が プロファイラーに対して、アセンブリがロード中であることを通知するために使用するコールバック メソッドを提供します。  
  
 [ICorProfilerCallback7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback7-interface.md)  
 共通言語ランタイムを使用してメモリ内のモジュールに関連付けられているシンボルのストリームが更新されたことをプロファイラーに通知するコールバック メソッドを提供します。  

[ICorProfilerCallback8 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-interface.md)  
共通言語ランタイムを使用して動的メソッドの JIT コンパイルが開始して完了したことをプロファイラーに通知するコールバック メソッドを提供します。

[ICorProfilerCallback9 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback9-interface.md)  
共通言語ランタイムを使用して動的メソッドは、ガベージ コレクションされ、その後にアンロードされたことをプロファイラーに通知するコールバック メソッドを提供します。

 [ICorProfilerFunctionControl インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)  
 コード プロファイラーが CLR と通信できるようにするためのメソッドを提供します。これは特定のメソッドを再コンパイルするときに、JIT コンパイラーがどのようにしてコードを生成するかを制御するためのものです。  
  
 [ICorProfilerFunctionEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 CLR で関数のコレクションを順番に反復処理するためのメソッドを提供します。  
  
 [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。  
  
 [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 .NET Framework 2.0 以降でサポートされるメソッドによって、`ICorProfilerInfo` インターフェイスを拡張します。  
  
 [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 `ICorProfilerInfo2` 以降でサポートされるメソッドによって、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)] インターフェイスを拡張します。  
  
 [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 コード プロファイラーが、イベントの監視および情報の要求を制御するために CLR との通信で使用するメソッドを提供します。  
  
 [ICorProfilerInfo5 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)  
 コード プロファイラーが、イベントの監視を制御するために CLR との通信で使用するメソッドを提供します。  
  
 [ICorProfilerInfo6 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)  
 指定された NGen モジュールに属していて、特定のメソッドの本体にインライン化ではないすべてのメソッドに列挙子を提供します。  
  
 [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)  
 新しくを適用するメソッドをモジュールにメタデータを定義して、メモリ内のシンボルのストリームへのアクセスを提供する提供します。  
  
 [ICorProfilerModuleEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 アプリケーションまたはプロファイラーによってロードされたモジュールのコレクションを順番に反復処理するためのメソッドを提供します。  
  
 [ICorProfilerObjectEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)  
 によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供します[Ngen.exe (ネイティブ イメージ ジェネレーター)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)します。  
  
 [ICorProfilerThreadEnum インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 CLR でスレッドのコレクションを順番に反復処理するためのメソッドを提供します。  
  
 [IMethodMalloc インターフェイス](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)  
 提供、[アロケーション](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-alloc-method.md)メソッドを新しい Microsoft intermediate language (MSIL) 関数本体にメモリを割り当てます。  
  
## <a name="related-sections"></a>関連項目  
 [プロファイルの概要](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
