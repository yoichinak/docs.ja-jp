---
title: StrongNameErrorInfo 関数
ms.date: 03/30/2017
api_name:
- StrongNameErrorInfo
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameErrorInfo
helpviewer_keywords:
- StrongNameErrorInfo function [.NET Framework strong naming]
ms.assetid: e91bf8c3-7c26-4732-938e-2e5b04abfc99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 021fa1668247bc59a4412d2b5f4bac3f5ee8cc6b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799116"
---
# <a name="strongnameerrorinfo-function"></a>StrongNameErrorInfo 関数
厳密な名前の関数のいずれかに基づいて最後に発生したエラー コードが取得されます。  
  
 この関数は非推奨とされます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameErrorInfo ();   
```  
  
## <a name="return-value"></a>戻り値  
 厳密な名前関数のいずれかによって設定された最後の COM エラーコード。  
  
## <a name="remarks"></a>Remarks  
 厳密な名前のメソッドのほとんどは、 `true`正常`false`に完了したかどうかを示す単純な値を返します。 `StrongNameErrorInfo`関数を使用して、厳密な名前関数によって生成された最後のエラーを指定する HRESULT を取得します。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
