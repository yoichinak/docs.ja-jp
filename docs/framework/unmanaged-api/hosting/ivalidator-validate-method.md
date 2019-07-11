---
title: IValidator::Validate メソッド
ms.date: 03/30/2017
api_name:
- IValidator.Validate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Validate
helpviewer_keywords:
- IValidator::Validate method [.NET Framework hosting]
- Validate method, IValidator interface [.NET Framework hosting]
ms.assetid: 7d68666a-fb73-4455-bebd-908d49a16abc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 840a3779ca5692787c2c352db60a29d6a4d4ba4f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768593"
---
# <a name="ivalidatorvalidate-method"></a>IValidator::Validate メソッド
指定したポータブル実行可能 (PE) または Microsoft intermediate language (MSIL) ファイルを検証します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Validate (  
    [in] IVEHandler            *veh,  
    [in] IUnknown              *pAppDomain,  
    [in] unsigned long          ulFlags,  
    [in] unsigned long          ulMaxError,  
    [in] unsigned long          token,  
    [in] LPWSTR                 fileName,  
    [in, size_is(ulSize)] BYTE *pe,  
    [in] unsigned long          ulSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `veh`  
 [in]ポインター、`IVEHandler`検証エラーを処理するインスタンス。  
  
 `pAppDomain`  
 [in]ファイルが読み込まれているアプリケーション ドメインへのポインター。  
  
 `ulFlags`  
 [in]ビットごとの組み合わせ[ValidatorFlags](../../../../docs/framework/unmanaged-api/hosting/validatorflags-enumeration.md)実行される検証を示す値。  
  
 `ulMaxError`  
 [in]検証を終了する前に許可されるエラーの最大数。  
  
 `token`  
 [in]使用されません。  
  
 `fileName`  
 [in]検証するファイルの名前を指定する文字列。  
  
 `pe`  
 [in]ファイルが格納されているメモリ バッファーへのポインター。  
  
 `ulSize`  
 [in]検証するファイルのバイト単位のサイズ。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** IValidator.idl, IValidator.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
