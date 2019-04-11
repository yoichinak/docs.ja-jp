---
title: ICorProfilerCallback6::GetAssemblyReferences メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c5296fbab71c67572718a58fedb9f89b064f816
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214690"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a>ICorProfilerCallback6::GetAssemblyReferences メソッド
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 共通言語ランタイムがアセンブリ参照クロージャのウォークを実行するときに、アセンブリがごく初期のローディング状態であることをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszAssemblyPath`  
 [in] メタデータが変更されるアセンブリのパスおよび名前。  
  
 `pAsmRefProvider`  
 [in]アドレスへのポインター、 [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)アセンブリを指定するインターフェイスの参照を追加します。  
  
## <a name="return-value"></a>戻り値  
 このコールバックからの戻り値は無視されます。  
  
## <a name="remarks"></a>Remarks  
 このコールバックは設定によって制御されます、 [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)イベント マスク フラグを呼び出すときに、 [ICorProfilerCallback5::SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)メソッド。 用のプロファイラーを登録する場合、 [icorprofilercallback 6::getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)コールバック メソッド、ランタイムへのポインターと共に読み込まれるアセンブリの名前とパスを渡します、 [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)メソッドへのインターフェイスのオブジェクト。 プロファイラーを呼び出すことが、 [icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)メソッドを`COR_PRF_ASSEMBLY_REFERENCE_INFO`で指定されたアセンブリから参照することを計画、各ターゲット アセンブリのオブジェクト、 `GetAssemblyReferences`コールバック。  
  
 `GetAssemblyReferences` コールバックを使用するのは、プロファイラーがアセンブリのメタデータを変更してアセンブリ参照を追加する必要がある場合のみです (でアセンブリのメタデータの実際の変更が実行されるに注意してください、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバック メソッドです)。プロファイラーは `GetAssemblyReferences` コールバック メソッドを実装して、モジュールがロードされたときにアセンブリ参照が追加されることを共通言語ランタイム (CLR) に知らせる必要があります。  これにより、プロファイラーが後でメタデータのアセンブリ参照を変更するつもりでも、アセンブリが共有している "初期の段階で CLR によって行われた決定" は有効なままになります。  このため一部のインスタンスでの、プロファイラーのメタデータ変更による `SECURITY_E_INCOMPATIBLE_SHARE` エラーの発生を回避できる場合があります。  
  
 プロファイラーを使用して、 [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md) CLR アセンブリ参照クロージャのウォーカーへのアセンブリ参照を追加するには、このメソッドが提供するオブジェクト。  [ICorProfilerAssemblyReferenceProvider](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)オブジェクトは、このコールバック内からのみ使用する必要があります。 呼び出し、 [icorprofilerassemblyreferenceprovider::addassemblyreference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)後のアセンブリ参照クロージャのウォークのみが変更されたメタデータは、このコールバックからのメソッドが生じません。 プロファイラーを使用する必要があります、 [IMetaDataAssemblyEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)内から明示的にアセンブリ参照を追加するオブジェクト、 [icorprofilercallback::moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)を参照するためのコールバックアセンブリ、実装している場合でも、`GetAssemblyReferences`コールバック。  
  
 プロファイラーは、同じアセンブリのこのコールバックに重複する呼び出しを受信することがあり、このような重複する呼び出しごとに同じ応答する必要があります (の同じセットを作成して[ICorProfilerAssemblyReferenceProvider:。AddAssemblyReference](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)呼び出し)。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback6 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-interface.md)
- [ModuleLoadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)
- [COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体](../../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
- [ICorProfilerAssemblyReferenceProvider インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-interface.md)
