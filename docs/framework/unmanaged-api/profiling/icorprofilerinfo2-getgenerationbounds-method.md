---
title: ICorProfilerInfo2::GetGenerationBounds メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433131"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds メソッド
各種ガベージ コレクション ジェネレーションを構成するメモリ領域 (ヒープのセグメント) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cObjectRanges`  
 [in] `ranges` 配列の呼び出し元によって割り当てられた要素の数。  
  
 `pcObjectRanges`  
 [out] その一部または全部が `ranges` 配列で返される範囲の総数を指定する整数へのポインター。  
  
 `ranges`  
 [out] An array of [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) structures, each of which describes a range (that is, block) of memory within the generation that is undergoing garbage collection.  
  
## <a name="remarks"></a>Remarks  
 ガベージ コレクションを処理中でない場合、`GetGenerationBounds` メソッドは任意のプロファイラー コールバックから呼び出すことができます。

 通常、ジェネレーションの移動はガベージ コレクション中に行われます。 コレクションの間にジェネレーションが増大する可能性はありますが、一般的に移動はありません。 したがって、`GetGenerationBounds` を呼び出す上で最も注目すべき地点は `ICorProfilerCallback2::GarbageCollectionStarted` と `ICorProfilerCallback2::GarbageCollectionFinished` の間です。  
  
 プログラムの起動中に、いくつかのオブジェクトが共通言語ランタイム (CLR) 自体によって割り当てられます。これは、一般的にはジェネレーションの 3 と 0 で行われます。 したがって、マネージド コードが実行を開始するまでに、これらのジェネレーションには既にオブジェクトが含まれています。 通常、ジェネレーションの 1 と 2 は、ガベージ コレクターによって生成されたダミー オブジェクトを除き、空です。 (The size of dummy objects is 12 bytes in 32-bit implementations of the CLR; the size is larger in 64-bit implementations.) You might also see generation 2 ranges that are inside modules produced by the Native Image Generator (NGen.exe). In this case, the objects in generation 2 are *frozen objects*, which are allocated when NGen.exe runs rather than by the garbage collector.  
  
 この関数は、呼び出し元が割り当てたバッファーを使用します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
