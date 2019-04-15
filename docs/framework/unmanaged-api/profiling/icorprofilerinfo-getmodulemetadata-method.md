---
title: ICorProfilerInfo::GetModuleMetaData メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 89a2424548bb577e3580d6eaa72f61e5cf9ccc7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111216"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a>ICorProfilerInfo::GetModuleMetaData メソッド
指定したモジュールにマップされるメタデータ インターフェイス インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a>パラメーター  
 `moduleId`  
 [in]インターフェイス インスタンスのマップされたモジュールの ID。  
  
 `dwOpenFlags`  
 [in]値、 [CorOpenFlags](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)マニフェスト ファイルを開くためのモードを指定する列挙体。 のみ、 `ofRead`、`ofWrite`と`ofNoTransform`のビットが無効です。  
  
 `riid`  
 [in]参照 ID (GUID) のメタデータ インターフェイスを持つインスタンスが取得されます。 参照してください[メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)インターフェイスの一覧についてはします。  
  
 `ppOut`  
 [out]メタデータ インターフェイス インスタンスのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 読み取り/書き込みモードで開かれるメタデータに問い合わせることができますが、その結果、プログラムのメタデータ、実行速度が、コンパイラからと同様に変更が加えられたため、メタデータは最適化できません。  
  
 メタデータを所有している (リソース モジュール) などの一部のモジュールはありません。 その場合、`GetModuleMetaData`は S_FALSE とで null 値の HRESULT 値を返します *`ppOut`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
