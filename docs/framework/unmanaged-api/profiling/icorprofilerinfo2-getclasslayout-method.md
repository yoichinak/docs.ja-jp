---
title: ICorProfilerInfo2::GetClassLayout メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5995eac780241b5d0a01b99b23ec91c2f325e2a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57478805"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a>ICorProfilerInfo2::GetClassLayout メソッド
指定したクラスで定義されるフィールドのメモリ内レイアウトに関する情報を取得します。 つまり、このメソッドはクラスのフィールドのオフセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a>パラメーター  
 `classID`  
 [in] レイアウトを取得するクラスの ID。  
  
 `rFieldOffset`  
 [入力、出力]配列の[COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md)トークンとクラスのフィールドのオフセットを含む各構造体。  
  
 `cFieldOffset`  
 [in] `rFieldOffset` 配列のサイズ。  
  
 `pcFieldOffset`  
 [out] 使用できる要素の総数へのポインター。 `cFieldOffset` が 0 である場合、この値は必要な要素の数を示します。  
  
 `pulClassSize`  
 [out] クラスのサイズ (バイト単位) を含む位置へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetClassLayout` メソッドは、クラス自体によって定義されているフィールドのみを返します。 クラスの親クラスもフィールドを定義している場合、プロファイラーは親クラスで `GetClassLayout` を呼び出してそのフィールドを取得する必要があります。  
  
 `GetClassLayout` を文字列クラスと一緒に使用する場合、このメソッドは E_INVALIDARG というエラー コードで失敗します。 使用[icorprofilerinfo 2::getstringlayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)文字列のレイアウトに関する情報を取得します。 `GetClassLayout` は、配列クラスを使用して呼び出される場合も失敗します。  
  
 `GetClassLayout` から制御が戻ったら、`rFieldOffset` バッファーのサイズが十分で、すべての使用可能な `COR_FIELD_OFFSET` 構造体を格納できたかどうかを確認する必要があります。 これを行うには、`pcFieldOffset` が指している値と、`rFieldOffset` のサイズを `COR_FIELD_OFFSET` 構造体のサイズで割った値を比較します。 `rFieldOffset` の大きさが十分でない場合は、`rFieldOffset` バッファーの割り当てを増やし、`cFieldOffset` を新しい大きいサイズに更新して、`GetClassLayout` を再度呼び出します。  
  
 別の方法として、最初に `GetClassLayout` を長さゼロの `rFieldOffset` バッファーで呼び出して、適切なバッファーのサイズを取得します。 その後、バッファーのサイズを `pcFieldOffset` で返された値に設定し、`GetClassLayout` を再度呼び出します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
