---
title: ISymUnmanagedSourceServerModule::GetSourceServerData メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedSourceServerModule.GetSourceServerData
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData
helpviewer_keywords:
- ISymUnmanagedSourceServerModule::GetSourceServerData method [.NET Framework debugging]
- GetSourceServerData method [.NET Framework debugging]
ms.assetid: 20bdf8ff-2d15-4c64-8950-6888f642d6c0
topic_type:
- apiref
ms.openlocfilehash: 6904271ed90cf733b9221178927bc680d76b58a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176579"
---
# <a name="isymunmanagedsourceservermodulegetsourceserverdata-method"></a>ISymUnmanagedSourceServerModule::GetSourceServerData メソッド
モジュールのソース サーバー データを返します。 呼び出し元は、`CoTaskMemFree`を使用してリソースを解放する必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSourceServerData(  
    [out] ULONG* pDataByteCount,
    [out, size_is (, *pDataByteCount)] BYTE** ppData);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pDataByteCount`  
 [アウト]ソース サーバー`ULONG32`データのサイズ (バイト単位) を受け取るを指すポインター。  
  
 `ppData`  
 [アウト]戻り`pDataByteCount`値へのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合はS_OK。それ以外の場合は、E_FAILまたはその他のエラー コードを返します。  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** コーシム.idl,コーシム.h  
  
## <a name="see-also"></a>関連項目

- [ISymUnmanagedSourceServerModule インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)
