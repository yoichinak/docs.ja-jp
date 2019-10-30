---
title: 'ICorProfilerInfo7:: ApplyMetaData メソッド'
ms.date: 02/15/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo7.ApplyMetaData
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: a1bfb649-4584-4d35-b3e6-8fe59b53992a
ms.openlocfilehash: 00d9bef1e2b59a2d2207d1e343380e0e81bee848
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130357"
---
# <a name="icorprofilerinfo7applymetadata-method"></a>ICorProfilerInfo7:: ApplyMetaData メソッド
[.NET Framework 4.6.1 以降のバージョンでのみでサポート]  
  
 `IMetadataEmit::Define*` メソッドによって新たに定義されたメタデータを、指定したモジュールに適用します。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT ApplyMetaData(  
        [in] ModuleID moduleID  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleID`  
 からメタデータが変更されたモジュールの識別子。  
  
## <a name="remarks"></a>Remarks  
 [Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバックの後にメタデータの変更が行われた場合は、新しいメタデータを使用する前にこのメソッドを呼び出す必要があります。  
  
 `ApplyMetaData` は、次の種類のメタデータの追加のみをサポートしています。  
  
- `AssemblyRef` レコードは、 [IMetaDataAssemblyEmit::D efineAssemblyRef](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)を呼び出すことによって作成します。 メソッドをオーバーライドします。  
  
- `TypeRef` レコードは、 [IMetaDataEmit::D efinetyperefbyname](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetyperefbyname-method.md)メソッドを呼び出すことによって作成します。  
  
- [IMetaDataEmit:: GetTokenFromTypeSpec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-gettokenfromtypespec-method.md)メソッドを呼び出すことによって作成するレコードを `TypeSpec` します。  
  
- `MemberRef` レコードは、 [IMetaDataEmit::D efinememberref](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definememberref-method.md)メソッドを呼び出すことによって作成します。  
  
- `MemberSpec` レコードは、 [IMetaDataEmit2::D efinemethodspec](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definemethodspec-method.md)メソッドを呼び出すことによって作成します。  
  
- `UserString` レコードは、 [IMetaDataEmit::D efineUserString](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineuserstring-method.md)メソッドを呼び出すことによって作成します。  

.NET Core 3.0 以降では、`ApplyMetaData` も次の型をサポートしています。

- `TypeDef` レコードは、 [IMetaDataEmit::D efineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md)メソッドを呼び出すことによって作成します。

- `MethodDef` レコードは、 [IMetaDataEmit::D efinemethod](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definemethod-method.md)メソッドを呼び出すことによって作成します。 ただし、既存の型に仮想メソッドを追加することはサポートされていません。 仮想メソッドは、 [Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)コールバックの前に追加する必要があります。

## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo7 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
