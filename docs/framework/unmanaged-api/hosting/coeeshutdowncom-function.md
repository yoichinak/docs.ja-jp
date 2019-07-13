---
title: CoEEShutDownCOM 関数
ms.date: 03/30/2017
api_name:
- CoEEShutDownCOM
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoEEShutDownCOM
helpviewer_keywords:
- CoEEShutDownCOM function [.NET Framework hosting]
ms.assetid: b634cae2-632f-4737-9be4-92d0652844d7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 74548df512f68761b006e064a6db968e82b03813
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779116"
---
# <a name="coeeshutdowncom-function"></a>CoEEShutDownCOM 関数
共通言語ランタイム (CLR) がランタイム呼び出し可能ラッパー (RCW) 内で保持しているすべてのインターフェイス ポインターを解放するを強制します。 RCW のすべてのキャッシュの解放の効果があります。 このグローバル関数は、.NET Framework 4 では非推奨とされます。 代わりに、特定のランタイムのエントリ ポイントを使用します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
void CoEEShutDownCOM ();  
```  
  
## <a name="remarks"></a>Remarks  
 `CoEEShutDownCOM`関数が最初にすべてのコンテキスト内とすべてのキャッシュにあるすべての Rcw を解放し、し、セットアップで既存の任意の終了処理通知を削除します。 DLL のアンロードは行われません。  
  
> [!CAUTION]
>  この関数では、プロセスに読み込まれるすべてのランタイムに影響します。  
  
 以降、.NET Framework 4 では、この関数に影響する特定のランタイムのエントリ ポイントを呼び出します。 エントリ ポイントを取得する、 [iclrruntimeinfo::getprocaddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)メソッド"CoEEShutDownCOM"を指定します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
