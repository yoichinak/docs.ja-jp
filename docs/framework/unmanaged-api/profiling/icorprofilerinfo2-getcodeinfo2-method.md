---
title: ICorProfilerInfo2::GetCodeInfo2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1acf77c250b47bb32a83227a427dd3fe4f909a33
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122487"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a>ICorProfilerInfo2::GetCodeInfo2 メソッド
指定した `FunctionID` に関連付けられているネイティブ コードの範囲を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionID`  
 [in] ネイティブ コードが関連付けられている関数の ID。  
  
 `cCodeInfos`  
 [in] `codeInfos` 配列のサイズ。  
  
 `pcCodeInfos`  
 [out]合計数へのポインター [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)構造体を使用できます。  
  
 `codeInfos`  
 [out] 呼び出し元が提供したバッファー。 メソッドから制御が戻った後で、それぞれがネイティブ コードのブロックを記述する `COR_PRF_CODE_INFO` の構造体の配列が含まれます。  
  
## <a name="remarks"></a>Remarks  
 エクステンとは Microsoft Intermediate Language (MSIL) オフセットの昇順に並べ替えられます。  
  
 `GetCodeInfo2` から制御が戻ったら、`codeInfos` バッファーのサイズが十分で、すべての `COR_PRF_CODE_INFO` 構造体を格納できたかどうかを確認する必要があります。 これを行うには、`cCodeInfos` の値を `cchName` パラメーターの値と比較します。 `COR_PRF_CODE_INFO` 構造体のサイズによって除算された `cCodeInfos` が `pcCodeInfos` より小さい場合は、`codeInfos` バッファーの割り当てを増やし、`cCodeInfos` を新しい大きいサイズに更新した後、`GetCodeInfo2` を再度呼び出します。  
  
 別の方法として、最初に `GetCodeInfo2` を長さゼロの `codeInfos` バッファーで呼び出して、適切なバッファーのサイズを取得します。 その後、`codeInfos` バッファーのサイズを、`pcCodeInfos` で返された値に `COR_PRF_CODE_INFO` 構造体のサイズを掛けた値に設定し、`GetCodeInfo2` を再度呼び出します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetCodeInfo3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
