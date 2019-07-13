---
title: IAssemblyName インターフェイス
ms.date: 03/30/2017
api_name:
- IAssemblyName
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyName
helpviewer_keywords:
- IAssemblyName interface [.NET Framework fusion]
ms.assetid: f7f8e605-6b67-4151-936f-f04ecd671d90
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0d8d59ef282818dd9852d0ff8d2ec2abd40986d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697928"
---
# <a name="iassemblyname-interface"></a>IAssemblyName インターフェイス
記述して、アセンブリの一意の id の操作のメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-clone-method.md)|これの簡易コピーを作成します。`IAssemblyName`オブジェクト。|  
|[Finalize メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-finalize-method.md)|これにより、`IAssemblyName`オブジェクト リソースを解放し、そのデストラクターが呼び出される前に、他のクリーンアップ操作を実行します。|  
|[GetDisplayName メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getdisplayname-method.md)|これによって参照されるアセンブリの人間が判読できる名前を取得`IAssemblyName`オブジェクト。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getname-method.md)|これによって参照されるアセンブリの単純な暗号化されていない名前を取得`IAssemblyName`オブジェクト。|  
|[GetProperty メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getproperty-method.md)|指定したによって参照されるプロパティにポインターを取得します。`PropertyId`します。|  
|[GetVersion メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-getversion-method.md)|これによって参照されるアセンブリのバージョン情報を取得`IAssemblyName`オブジェクト。|  
|[IsEqual メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-isequal-method.md)|指定したかどうかを判断します`IAssemblyName`オブジェクトがこれと等しい`IAssemblyName`を基に、指定した比較フラグ。|  
|[SetProperty メソッド](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-setproperty-method.md)|指定したによって参照されるプロパティの値を設定`PropertyId`します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion.h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
- [IAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)
