---
title: ICorProfilerInfo3::GetRuntimeInformation メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetRuntimeInformation Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetRuntimeInformation
helpviewer_keywords:
- GetRuntimeInformation method [.NET Framework profiling]
- ICorProfilerInfo3::GetRuntimeInformation method [.NET Framework profiling]
ms.assetid: 4400fb8c-0407-4791-8557-f011fd2aee51
topic_type:
- apiref
ms.openlocfilehash: 20556d85655a0a1bbe069a94b99c19c774a13ce6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449685"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation メソッド
Provides version information about the common language runtime (CLR) that is being profiled.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetRuntimeInformation(  
       [out] USHORT *pClrInstanceId,  
       [out] COR_PRF_RUNTIME_TYPE *pRuntimeType,  
       [out] USHORT *pMajorVersion,  
       [out] USHORT *pMinorVersion,  
       [out] USHORT *pBuildNumber,  
       [out] USHORT *pQFEVersion,  
       [in]  ULONG  cchVersionString,  
       [out] ULONG  *pcchVersionString,  
       [out, size_is(cchVersionString), length_is(*pcchVersionString)]  
                   WCHAR  szVersionString[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pClrInstanceId`  
 [out] The representative ID of a running CLR instance in a process. This is the same as the `ClrInstanceID` that the event tracing for Windows (ETW) startup event reports.  
  
 `pRuntimeType`  
 [out] The runtime type. This parameter returns `COR_PRF_DESKTOP_CLR` for the desktop version of the CLR, or `COR_PRF_CORE_CLR` for the core version of the CLR used in Silverlight.  
  
 `pMajorVersion`  
 [out] The major version number of the CLR.  
  
 `pMinorVersion`  
 [out] The minor version number of the CLR.  
  
 `pBuildVersion`  
 [out] The build version number of the CLR.  
  
 `pQFEVersion`  
 [out] The version number of the CLR that is associated with a software update.  
  
 `cchVersionString`  
 [in] The length, in characters, of the buffer that `szVersionString` points to.  
  
 `pcchVersionString`  
 [out] The length, in characters, of `szVersionString`.  
  
 `szVersionString`  
 [out] The CLR version string.  
  
## <a name="remarks"></a>Remarks  
 You may pass null for any parameter. However, `pcchVersionString` cannot be null unless `szVersionString` is also null.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
