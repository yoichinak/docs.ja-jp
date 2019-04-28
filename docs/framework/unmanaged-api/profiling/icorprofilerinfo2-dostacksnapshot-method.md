---
title: ICorProfilerInfo2::DoStackSnapshot メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.DoStackSnapshot
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::DoStackSnapshot
helpviewer_keywords:
- ICorProfilerInfo2::DoStackSnapshot method [.NET Framework profiling]
- DoStackSnapshot method [.NET Framework profiling]
ms.assetid: 287b11e9-7c52-4a13-ba97-751203fa97f4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 12ef215253ca02048a5a3fc2c7c682823233929f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779822"
---
# <a name="icorprofilerinfo2dostacksnapshot-method"></a>ICorProfilerInfo2::DoStackSnapshot メソッド
指定されたスレッドのスタックでマネージド フレームをについて説明し、コールバックを通じてプロファイラーに情報を送信します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DoStackSnapshot(  
    [in] ThreadID thread,  
    [in] StackSnapshotCallback *callback,  
    [in] ULONG32 infoFlags,  
    [in] void *clientData,  
    [in, size_is(contextSize), length_is(contextSize)] BYTE context[],  
    [in] ULONG32 contextSize);  
```  
  
## <a name="parameters"></a>パラメーター  
 `thread`  
 [in]対象のスレッドの ID。  
  
 Null を渡す`thread`現在のスレッドのスナップショットが生成されます。 場合、`ThreadID`の別のスレッドが渡される、共通言語ランタイム (CLR) スレッドを中断します、スナップショットの実行が再開されます。  
  
 `callback`  
 [in]実装へのポインター、 [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)メソッドで、各マネージ フレームとフレームの非管理対象の各実行に関する情報をプロファイラーを提供する、CLR によって呼び出されます。  
  
 `StackSnapshotCallback`メソッド プロファイラー ライターによって実装されます。  
  
 `infoFlags`  
 [in]値、 [COR_PRF_SNAPSHOT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-snapshot-info-enumeration.md)によって各フレームを渡されるデータの量を指定する列挙体`StackSnapshotCallback`します。  
  
 `clientData`  
 [in]直接渡されるクライアントのデータへのポインター、`StackSnapshotCallback`コールバック関数。  
  
 `context`  
 [in]Win32 へのポインター`CONTEXT`構造体は、スタック ウォークをシードするために使用します。 Win32`CONTEXT`構造は、CPU レジスタの値が含まれています、特定の時点で、CPU の状態を表します。  
  
 シードにより、CLR がスタックの先頭がアンマネージ ヘルパー コードの場合、スタック ウォークを開始する場所を決定します。それ以外の場合、シードは無視されます。 非同期のウォークのシードを指定する必要があります。 同期のウォークを実行している場合、シードの必要はありません。  
  
 `context`パラメーターは COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効ですが、`infoFlags`パラメーター。  
  
 `contextSize`  
 [in]サイズ、`CONTEXT`によって参照されている構造体、`context`パラメーター。  
  
## <a name="remarks"></a>Remarks  
 Null を渡す`thread`現在のスレッドのスナップショットが生成されます。 時に対象のスレッドが中断されている場合にのみ、他のスレッドのスナップショットを作成できます。  
  
 プロファイラーは、スタック ウォークが、ときに呼び出す`DoStackSnapshot`します。 CLR がその呼び出しから戻る前に呼び出し、`StackSnapshotCallback`を複数回 1 回ごとに管理されているフレーム (または非管理対象のフレームの実行)、スタックにします。 非管理対象のフレームが発生したときを自分でに説明する必要があります。  
  
 スタックが走査され、順序が逆の方法、フレームがスタックにプッシュされた: 最後 (最後にプッシュされた) 最初に、メイン (最初にプッシュされた) フレームをリーフします。  
  
 プロファイラーでマネージ スタックをプログラムする方法の詳細については、次を参照してください。 [、.NET Framework 2.0 における Profiler スタック ウォーク。基本、そしてその向こう](https://go.microsoft.com/fwlink/?LinkId=73638)します。  
  
 スタック ウォークには、次のセクションで説明するよう同期または非同期でを指定できます。  
  
## <a name="synchronous-stack-walk"></a>同期スタック ウォーク  
 同期スタック ウォークは、コールバックへの応答で、現在のスレッドのスタックをウォークします。 シード処理または中断は必要ありません。  
  
 同期を行うときに、プロファイラーのいずれかを呼び出して、CLR への応答を呼び出す[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) (または[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) メソッドを呼び出す`DoStackSnapshot`のスタック ウォーク、現在のスレッド。 これは、スタックがどのように通知でなどを表示する場合に便利です[icorprofilercallback::objectallocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)します。 呼び出すだけで`DoStackSnapshot`内から、`ICorProfilerCallback`で null を渡す場合、メソッド、`context`と`thread`パラメーター。  
  
## <a name="asynchronous-stack-walk"></a>非同期のスタック ウォーク  
 別のスレッドのスタックや、応答が現在のスレッドの命令ポインターをハイジャックして、コールバックではなく、現在のスレッドのスタックをウォーク、非同期のスタック ウォークする必要があります。 非同期のチュートリアルでは、アンマネージ コード、プラットフォームの一部でない場合は、スタックの一番上のシードの呼び出し (PInvoke) が必要です、COM の呼び出しでも CLR 自体でヘルパー コード。 たとえば、ジャストイン タイム (JIT) コンパイルやガベージ コレクションを実行するコードは、ヘルパー コードです。  
  
 直接対象のスレッドを中断することによって、シードを取得し、自分で、最上位に表示されるまでにマネージ フレーム スタックを走査します。 対象のスレッドが中断された後は、対象のスレッドの現在のレジスタのコンテキストを取得します。 次に、呼び出すことでレジスタのコンテキストがアンマネージ コードを指すかどうかを決定[icorprofilerinfo::getfunctionfromip](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md) -返された場合、 `FunctionID` 0 に等しい、フレームがアンマネージ コード。 最初のマネージ フレームに到達し、そのフレームのレジスタのコンテキストに基づき、シードのコンテキストを計算するまで、スタックについて説明します。  
  
 呼び出す`DoStackSnapshot`非同期スタック ウォークを開始する、シードのコンテキストを使用します。 シードを指定しない場合`DoStackSnapshot`スタックの上部にあるマネージ フレームをスキップする場合があり、その結果は、スタック ウォークが不完全です。 シードを指定した場合は、JIT コンパイルまたはネイティブ イメージ ジェネレーター (Ngen.exe) を指している必要があります-生成されたコードです。それ以外の場合、 `DoStackSnapshot` CORPROF_E_STACKSNAPSHOT_UNMANAGED_CTX エラー コードを返します。  
  
 非同期のスタック ウォークを簡単にデッドロックが発生するか、アクセス違反が次のガイドラインに従わない場合、します。  
  
- 直接のスレッドを中断する場合は、マネージ コードを実行しないが、スレッドが別のスレッドを中断できますを注意してください。  
  
- 常にブロック、 [icorprofilercallback::threaddestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)スレッドのスタック ウォークが完了するまでのコールバック。  
  
- プロファイラーがガベージ コレクションをトリガーできる CLR 関数を呼び出すときに、ロックを保持しないでください。 つまり、所有元のスレッドがガベージ コレクションをトリガーする呼び出しを行う場合、ロックを保持しないでください。  
  
 またがデッドロックの危険性を呼び出す場合`DoStackSnapshot`プロファイラーが別のターゲット スレッドのスタックを学ぶことができるように作成したスレッドから。 最初に作成したスレッドが特定`ICorProfilerInfo*`メソッド (含む`DoStackSnapshot`)、CLR はスレッドごと、そのスレッドで CLR 固有の初期化を実行します。 プロファイラーには、スタック ウォーク、しようとして対象のスレッドが中断されている場合、およびその対象スレッドは、このスレッドごとの初期化を実行するために必要なロックを所有するが発生した場合は、デッドロックが発生します。 このデッドロックを回避することを最初の呼び出しに`DoStackSnapshot`からプロファイラーが作成したスレッドについて説明しますが、別が対象に、スレッドは、まず対象のスレッドを中断しないようにします。 この最初の呼び出しにより、スレッドごとの初期化がデッドロックなしで完了できます。 場合`DoStackSnapshot`が成功し、少なくとも 1 つのフレームを報告その後、対象のスレッドと呼び出しを中断するプロファイラーが作成したスレッドの安全ななります`DoStackSnapshot`ターゲット スレッドのスタック ウォークします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
