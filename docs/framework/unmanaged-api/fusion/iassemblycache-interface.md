---
title: IAssemblyCache インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyCache
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache
helpviewer_keywords:
- IAssemblyCache interface [.NET Framework fusion]
ms.assetid: 71ea170f-872d-4fc5-81b6-27da1dec9b19
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6dab5fe941fce3c23ba718906b29c80c6d257c2f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796770"
---
# <a name="iassemblycache-interface"></a>IAssemblyCache インターフェイス
Fusion テクノロジによって使用されるグローバルアセンブリキャッシュを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateAssemblyCacheItem メソッド](iassemblycache-createassemblycacheitem-method.md)|新しい[Iassemblycacheitem](iassemblycacheitem-interface.md)への参照を取得します。|  
|[CreateAssemblyScavenger メソッド](iassemblycache-createassemblyscavenger-method.md)|Fusion テクノロジによる内部使用のために予約されています。|  
|[InstallAssembly メソッド](iassemblycache-installassembly-method.md)|指定したアセンブリをグローバルアセンブリキャッシュにインストールします。|  
|[QueryAssemblyInfo メソッド](iassemblycache-queryassemblyinfo-method.md)|指定したアセンブリに関する要求されたデータを取得します。|  
|[UninstallAssembly メソッド](iassemblycache-uninstallassembly-method.md)|指定したアセンブリをグローバルアセンブリキャッシュからアンインストールします。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [グローバル アセンブリ キャッシュ](../../app-domains/gac.md)
