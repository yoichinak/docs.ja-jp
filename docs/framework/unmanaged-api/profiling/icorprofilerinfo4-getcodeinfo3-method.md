---
title: ICorProfilerInfo4::GetCodeInfo3 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb067d16ef7f8177f979a083707f8c6ef36750c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61685629"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a>ICorProfilerInfo4::GetCodeInfo3 メソッド
指定した関数の JIT 再コンパイル バージョンに関連付けられているネイティブ コードの範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionID`  
 [in] ネイティブ コードが関連付けられている関数の ID。  
  
 `reJitId`  
 [in] JIT 再コンパイルされた関数のID。  
  
 `cCodeInfos`  
 [in] `codeInfos` 配列のサイズ。  
  
 `pcCodeInfos`  
 [out]合計数へのポインター [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体を使用できます。  
  
 `codeInfos`  
 [out] 呼び出し元が提供したバッファー。 メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。  
  
## <a name="remarks"></a>Remarks  
 `GetCodeInfo3`メソッドは[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)を指定した IP アドレスを含む関数の JIT 再コンパイルの ID を取得できる点を除いて、します。  
  
> [!NOTE]
>  `GetCodeInfo3` 一方、ガベージ コレクションをトリガーできる[GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)されません。 詳細については、次を参照してください。、 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT。  
  
 エクステントは共通中間言語 (CIL) オフセットの昇順に並べ替えられます。  
  
 後`GetCodeInfo3`返されることを確認する必要があります、`codeInfos`バッファーのすべてを格納するのに十分な大きさが、 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体。 これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。 場合`cCodeInfos`のサイズで割った、 [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造がより小さい`pcCodeInfos`、割り当てを増やし`codeInfos`バッファーは、更新`cCodeInfos`呼び出しと新しい大きいサイズで`GetCodeInfo3`もう一度です。  
  
 別の方法として、最初に `GetCodeInfo3` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。 設定することができます、`codeInfos`バッファー サイズの戻り値に`pcCodeInfos`のサイズを乗算を[COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造、および呼び出し`GetCodeInfo3`もう一度です。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetCodeInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
