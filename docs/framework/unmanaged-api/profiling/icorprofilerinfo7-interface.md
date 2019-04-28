---
title: ICorProfilerInfo7 インターフェイス
ms.date: 03/30/2017
ms.assetid: cf37c462-73c5-412a-a7f8-bb26ca746313
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d8586031c5bcb0303a64b67ee601fe41b81ee3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786244"
---
# <a name="icorprofilerinfo7-interface"></a>ICorProfilerInfo7 インターフェイス
[[!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] 以降のバージョンでサポート]  
  
 サブクラス[ICorProfilerInfo6](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)新しくを適用するメソッドをモジュールにメタデータを定義して、メモリ内のシンボルのストリームへのアクセスを提供するを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[ApplyMetaData メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md)|新しく定義されたメタデータを適用、`IMetadataEmit::Define*`メソッドが指定されたモジュールにします。|  
|[GetInMemorySymbolsLength メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md)|メモリ内のシンボルのストリームの長さを返します。|  
|[ReadInMemorySymbols](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md)|メモリ内のシンボルのストリームからバイトを読み取ります。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
