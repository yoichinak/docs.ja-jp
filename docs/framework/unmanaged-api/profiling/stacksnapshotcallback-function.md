---
title: StackSnapshotCallback 関数
ms.date: 03/30/2017
api_name:
- StackSnapshotCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- StackSnapshotCallback
helpviewer_keywords:
- StackSnapshotCallback function [.NET Framework profiling]
ms.assetid: d0f235b2-91fe-4f82-b7d5-e5c64186eea8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 43e71696282a3c9e6d25793b583ee19f306e167b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486239"
---
# <a name="stacksnapshotcallback-function"></a>StackSnapshotCallback 関数
によって開始されるスタック ウォーク中にスタックの各マネージ フレームとフレームの非管理対象の各実行に関する情報を使用してプロファイラーを提供、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT __stdcall StackSnapshotCallback (  
    [in] FunctionID funcId,  
    [in] UINT_PTR ip,  
    [in] COR_PRF_FRAME_INFO frameInfo,  
    [in] ULONG32 contextSize,  
    [in] BYTE context[],  
    [in] void *clientData  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `funcId`  
 [in]この値が 0 の場合は、このコールバックは非管理対象のフレームの実行それ以外の場合、マネージ関数の識別子は、このコールバック マネージ フレームです。  
  
 `ip`  
 [in]フレームのネイティブ コードの命令ポインターの値。  
  
 `frameInfo`  
 [in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を参照する値。 この値は、このコールバック中にのみ使用して有効です。  
  
 `contextSize`  
 [in]サイズ、`CONTEXT`によって参照されている構造体、`context`パラメーター。  
  
 `context`  
 [in]Win32 へのポインター`CONTEXT`このフレームの cpu 使用率の状態を表す構造体です。  
  
 `context`パラメーターは COR_PRF_SNAPSHOT_CONTEXT フラグが渡された場合にのみ有効です。`ICorProfilerInfo2::DoStackSnapshot`します。  
  
 `clientData`  
 [in]直接渡されるクライアント データへのポインター`ICorProfilerInfo2::DoStackSnapshot`します。  
  
## <a name="remarks"></a>Remarks  
 `StackSnapshotCallback`関数がプロファイラー ライターによって実装されます。 実行される作業の複雑さを制限する必要があります`StackSnapshotCallback`します。 たとえばを使用する場合`ICorProfilerInfo2::DoStackSnapshot`非同期で対象のスレッドが保持してロックします。 場合内のコード`StackSnapshotCallback`同じのロックが必要です、デッドロック、議論が生じる可能性があります。  
  
 `ICorProfilerInfo2::DoStackSnapshot`メソッドの呼び出し、`StackSnapshotCallback`関数のマネージ フレームごとに 1 回または 1 回あたりアンマネージ フレームの実行。 場合`StackSnapshotCallback`呼びますプロファイラーの非管理対象のフレームの実行、レジスタのコンテキストを使用できます (によって参照される、`context`パラメーター)、独自のアンマネージ スタック ウォークを実行します。 この場合は、Win32`CONTEXT`構造体が最後にプッシュされたフレーム アンマネージ フレームの実行中の CPU の状態を表します。 ただし、Win32`CONTEXT`構造体には、すべてのレジスタの値が含まれています、フレーム ポインター レジスタ、スタック ポインター レジスタ、命令ポインター レジスタ、および (つまり、保持された) 不揮発性の値にのみ依存する必要があります整数レジスタします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [DoStackSnapshot メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
