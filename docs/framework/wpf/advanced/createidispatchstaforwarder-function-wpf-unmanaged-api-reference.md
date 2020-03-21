---
title: 関数を呼び出す - WPF アンマネージ API リファレンス
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CreateIDispatchSTAForwarder
api_location:
- PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
ms.openlocfilehash: e151ffa6eb5f1dc7479c699e0d7f9f3f57833ebd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174720"
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a>関数を作成します (WPF アンマネージ API リファレンス)
この API は、Windows プレゼンテーション基盤 (WPF) インフラストラクチャをサポートし、コードから直接使用することを意図していません。  
  
 スレッドおよびウィンドウ管理用の Windows プレゼンテーション 基盤 (WPF) インフラストラクチャで使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,
   __deref_out IDispatch **ppForwarder  
)  
```  
  
## <a name="parameters"></a>パラメーター  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 ディスパッチデリゲート  
 `IDispatch`インターフェイスへのポインター。  
  
 ppフォワー  
 `IDispatch`インターフェイスのアドレスへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[NET Framework のシステム要件](../../get-started/system-requirements.md)を参照してください。  
  
 **Dll：**  
  
 NET フレームワーク 3.0 および 3.5: プレゼンテーションホストDLL.dll  
  
 NET フレームワーク 4 以降の場合: PresentationHost_v0400.dll  
  
 **.NET フレームワーク のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [WPF のアンマネージ API リファレンス](wpf-unmanaged-api-reference.md)
