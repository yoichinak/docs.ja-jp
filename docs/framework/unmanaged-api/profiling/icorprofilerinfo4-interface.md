---
title: ICorProfilerInfo4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 177e5ef8054f408dc8ec3475c56043394a636bc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049454"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 インターフェイス
コード プロファイラーが共通言語ランタイム (CLR) イベントの監視を制御する、要求の情報との通信に使用するメソッドを提供します。 . `ICorProfilerInfo4`インターフェイスは、その他の拡張機能`ICorProfilerInfo`インターフェイス。 追加された、・ イン タイム (JIT) の再コンパイルをサポートする新しいメソッドを提供しますが、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumJITedFunctions2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|以前に JIT コンパイル、JIT 再コンパイルしていたすべての関数の列挙子を返します。|  
|[EnumThreads メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|プロファイリングされたプロセスのすべてのマネージ スレッドのコレクションを順番に反復処理するメソッドを提供する列挙子を取得します。|  
|[GetCodeInfo3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。|  
|[GetFunctionFromIP2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|マネージ コードの命令ポインターを指定された関数の JIT 再コンパイル バージョンにマップします。|  
|[GetILToNativeMapping2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Microsoft intermediate language (MSIL) オフセットを指定した関数の JIT 再コンパイル バージョンに含まれるコードのネイティブ オフセットへのマップを取得します。|  
|[GetObjectSize2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|指定したオブジェクトのサイズを返します。|  
|[GetReJITIDs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|JIT 再コンパイルのすべてのバージョン指定の関数も割り当てられているを識別する Id の配列を返します。|  
|[InitializeCurrentThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|後続のプロファイラー API は、デッドロックを回避するため、同じスレッドで呼び出しの前に、現在のスレッドを初期化します。|  
|[RequestReJIT メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|指定された関数のすべてのインスタンスの JIT 再コンパイルを要求します。|  
|[RequestRevert メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|指定された関数のすべてのインスタンスを元のバージョンに戻します。|  
  
## <a name="remarks"></a>Remarks  
 CLR は、`ICorProfilerInfo4` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
