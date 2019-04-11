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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a13e3e525c7f019e7dc49111b88ac374345830af
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164932"
---
# <a name="icorprofilerinfo3getruntimeinformation-method"></a>ICorProfilerInfo3::GetRuntimeInformation メソッド
プロファイリングされている共通言語ランタイム (CLR) のバージョンについて説明します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [out]プロセスで実行中の CLR インスタンスの担当者の ID。 これと同じ、 `ClrInstanceID` Windows (ETW) のスタートアップ イベント トレーシングのイベントをレポートすることです。  
  
 `pRuntimeType`  
 [out]ランタイム型。 このパラメーターを返します`COR_PRF_DESKTOP_CLR`、CLR のデスクトップ バージョンのまたは`COR_PRF_CORE_CLR`Silverlight で使用されている CLR の core バージョン。  
  
 `pMajorVersion`  
 [out]CLR のメジャー バージョン番号。  
  
 `pMinorVersion`  
 [out]CLR のマイナー バージョン番号。  
  
 `pBuildVersion`  
 [out]CLR のビルド バージョン番号。  
  
 `pQFEVersion`  
 [out]ソフトウェア更新プログラムに関連付けられている CLR のバージョン番号。  
  
 `cchVersionString`  
 [in]バッファーの文字の長さを`szVersionString`を指します。  
  
 `pcchVersionString`  
 [out]長さを文字単位の`szVersionString`します。  
  
 `szVersionString`  
 [out]CLR バージョン文字列です。  
  
## <a name="remarks"></a>Remarks  
 任意のパラメーターに null を渡すことがあります。 ただし、 `pcchVersionString` null にすることはできませんしない限り、`szVersionString`も null です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
