---
title: ICorProfilerObjectEnum インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92370751b38029435b12c177b75cd4d9402369b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220943"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum インターフェイス
によって生成される固定されたオブジェクトのコレクションを順番に反復処理するメソッドを提供します、 [Ngen.exe (ネイティブ イメージ ジェネレーター)](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|この `ICorProfilerObjectEnum` インターフェイスのコピーへのインターフェイス ポインターを取得します。|  
|[GetCount メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|コレクション内で固定オブジェクトの合計数を取得します。|  
|[Next メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|列挙子の現在の位置から、オブジェクトのシーケンシャル コレクションから指定した数の隣接するオブジェクトを取得します。|  
|[Reset メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|この列挙子のカーソルをシーケンスの開始位置に移動します。|  
|[Skip メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|指定した要素数がスキップされるように、現在の位置からこの列挙子のカーソルを進めます。|  
  
## <a name="remarks"></a>Remarks  
 `ICorProfilerObjectEnum` インターフェイスは列挙子です。 このインターフェイスにより、配列の受信側は、受信側に適した速度で送信側から要素をプルできます。 つまり、受信側は配列の要素のフローを明示的に制御できる大きな配列をメソッド パラメーターとして渡すことに関連する問題を回避します。  
  
 使用[icorprofilerinfo 2::enummodulefrozenobjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)へのポインターを取得する、`ICorProfilerObjectEnum`インターフェイス。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModuleFrozenObjects メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
