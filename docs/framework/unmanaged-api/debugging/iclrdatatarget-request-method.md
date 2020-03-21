---
title: ICLRDataTarget::Request メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.Request
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::Request
helpviewer_keywords:
- ICLRDataTarget::Request method [.NET Framework debugging]
- Request method [.NET Framework debugging]
ms.assetid: 4723bd1c-eddb-4ed2-897a-010024a47e01
topic_type:
- apiref
ms.openlocfilehash: 336ba38bc80fcb2649a12c78691e52c5e4d70bfe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179110"
---
# <a name="iclrdatatargetrequest-method"></a>ICLRDataTarget::Request メソッド
共通言語ランタイム (CLR) データ アクセス サービスによって呼び出され、実装で定義されている操作を要求します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Request (  
    [in] ULONG32            reqCode,  
    [in] ULONG32            inBufferSize,  
    [in, size_is(inBufferSize)]
        BYTE                *inBuffer,  
    [in] ULONG32            outBufferSize,  
    [out, size_is(outBufferSize)]
        BYTE                *outBuffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `reqCode`  
 [in]ユーザー定義。  
  
 `inBufferSize`  
 [in]入力要求に使用される入力バッファーのサイズ。  
  
 `inBuffer`  
 [in]要求を含むバッファー。  
  
 `outBufferSize`  
 [in]応答に使用される出力バッファーのサイズ。  
  
 `outBuffer`  
 [アウト]応答を含むバッファー。  
  
## <a name="remarks"></a>解説  
 この`Request`メソッドは、指定されていないカスタム操作の追加を容易にします。 つまり、このメソッドは、インターフェイス定義のリビジョンを必要とせずに機能拡張を提供します。  
  
 このメソッドは、デバッグ アプリケーションの作成者によって実装されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** をします。  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRDataTarget インターフェイス](iclrdatatarget-interface.md)
