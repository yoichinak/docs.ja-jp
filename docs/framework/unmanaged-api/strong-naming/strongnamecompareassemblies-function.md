---
title: StrongNameCompareAssemblies 関数
ms.date: 03/30/2017
api_name:
- StrongNameCompareAssemblies
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameCompareAssemblies
helpviewer_keywords:
- StrongNameCompareAssemblies function [.NET Framework strong naming]
ms.assetid: 763f2375-efc6-4219-8806-a3b0567ef72b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd3813d977f94db4168da8c888485b323f4072ad
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471278"
---
# <a name="strongnamecompareassemblies-function"></a>StrongNameCompareAssemblies 関数
厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamecompareassemblies](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameCompareAssemblies (  
    [in]  LPCWSTR   wszAssembly1,  
    [in]  LPCWSTR   wszAssembly2,  
    [out] DWORD     *pdwResult  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszAssembly1`  
 [in]最初のアセンブリへのパス。  
  
 `wszAssembly2`  
 [in]2 つ目のアセンブリへのパス。  
  
 `pdwResult`  
 [out]次の値のいずれか:  
  
-   `SN_CMP_DIFFERENT` (0) のアセンブリが別のデータを含むことを指定します。  
  
-   `SN_CMP_IDENTICAL` (1) - アセンブリが、署名とチェックサムも含めて一致ではことを指定します。  
  
-   `SN_CMP_SIGONLY` (2) のアセンブリが署名とチェックサムによってのみが異なることを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="remarks"></a>Remarks  
 アセンブリの厳密な名前の署名は、アセンブリのテキスト名、バージョン、カルチャ、および公開キー トークンで構成されます。  
  
 場合、`StrongNameCompareAssemblies`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="see-also"></a>関連項目
- [StrongNameCompareAssemblies メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamecompareassemblies-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
