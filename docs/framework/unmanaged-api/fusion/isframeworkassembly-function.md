---
title: IsFrameworkAssembly 関数
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 269e3702c21532f377735ba6087abb1603dde4f7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796318"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly 関数
指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzAssemblyReference`  
 から確認するアセンブリの名前。  
  
 `pbIsFrameworkAssembly`  
 入出力アセンブリが管理されているかどうかを示すブール値。  
  
 `pwzFrameworkAssemblyIdentity`  
 からアセンブリの一意の id を含む、正規化されていない文字列。  
  
 `pccSize`  
 [入力] `pwzFrameworkAssemblyIdentity` のサイズ。  
  
## <a name="remarks"></a>Remarks  
 `pwzAssemblyReference`パラメーターは、アセンブリの名前を含む文字列へのポインターです。  
  
 このアセンブリが .NET Framework の一部である場合、 `pbIsFrameworkAssembly`パラメーターにはの`true`ブール値が格納されます。  
  
 名前付きアセンブリが .NET Framework に含まれていない場合、また`pwzAssemblyReference`はパラメーターがアセンブリの名前を`pbIsFrameworkAssembly`指定しない場合、に`false`はブール値のが格納されます。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
## <a name="see-also"></a>関連項目

- [Fusion グローバル静的関数](fusion-global-static-functions.md)
