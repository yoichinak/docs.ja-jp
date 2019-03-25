---
title: ICorProfilerCallback::MovedReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ca0d1c647ed23d9540377068b7fd75fbb88bdfeb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480755"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences メソッド
圧縮ガベージ コレクションを実行した後の、ヒープ内のオブジェクトの新しいレイアウトを報告するために呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>パラメーター  
 `cMovedObjectIDRanges`  
 [in] 圧縮ガベージ コレクションを実行した後に移動される、隣接したオブジェクトのブロック数。 つまり、`cMovedObjectIDRanges` の値は `oldObjectIDRangeStart`、`newObjectIDRangeStart`、および `cObjectIDRangeLength` 配列の合計サイズです。  
  
 `MovedReferences` の次の 3 つの引数は並列配列です。 つまり、`oldObjectIDRangeStart[i]`、`newObjectIDRangeStart[i]`、`cObjectIDRangeLength[i]` はすべて、隣接するオブジェクトの同じブロックを対象としています。  
  
 `oldObjectIDRangeStart`  
 [in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの古い (ガベージ コレクション実行前の) 開始アドレスを表す、`ObjectID` 値の配列。  
  
 `newObjectIDRangeStart`  
 [in] それぞれがメモリ内の有効な隣接オブジェクト ブロックの新しい (ガベージ コレクション実行後の) 開始アドレスを表す、`ObjectID` 値の配列。  
  
 `cObjectIDRangeLength`  
 [in] それぞれがメモリ内の隣接オブジェクト ブロックのサイズを表す、整数の配列。  
  
 サイズは、`oldObjectIDRangeStart` および `newObjectIDRangeStart` 配列内の参照される各ブロックに対して指定します。  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]
>  このメソッドは、64 ビット プラットフォームで 4 GB より大きいオブジェクトのサイズを `MAX_ULONG` として報告します。 4 GB より大きいオブジェクトのサイズを取得する、 [icorprofilercallback 4::movedreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)メソッド代わりにします。  
  
 圧縮ガベージ コレクターは、無効なオブジェクトによって占有されているメモリを解放し、解放された領域を圧縮します。 その結果、ヒープ内で有効なオブジェクトが移動され、以前の通知で配布された `ObjectID` の値が変更されることがあります。  
  
 既存の `ObjectID` の値 (`oldObjectID`) が次の範囲内にあるとします。  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 この場合、範囲の開始からオブジェクトの開始までのオフセットは次のとおりです。  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 `i` の値が次の範囲内にあるとします。  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 この場合、新しい `ObjectID` は次のように計算できます。  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 ガーベッジ コレクションでオブジェクトが古い場所から新しい場所へ移動中の可能性があるため、コールバックの間は `MovedReferences` によって渡される `ObjectID` 値はすべて無効です。 このため、`MovedReferences` 呼び出しの間、プロファイラーはオブジェクトを検査するべきではありません。 A [icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)コールバックは、の新しい場所に移動されたすべてのオブジェクトを検査を実行できることを示します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
