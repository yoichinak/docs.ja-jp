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
ms.openlocfilehash: aee9b986c1e26c1b2e34dac7151a00172451bbad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796553"
---
# <a name="iassemblyname-interface"></a>IAssemblyName インターフェイス
アセンブリの一意の id を記述および操作するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Clone メソッド](iassemblyname-clone-method.md)|この`IAssemblyName`オブジェクトの簡易コピーを作成します。|  
|[Finalize メソッド](iassemblyname-finalize-method.md)|この`IAssemblyName`オブジェクトが、デストラクターが呼び出される前にリソースを解放し、その他のクリーンアップ操作を実行できるようにします。|  
|[GetDisplayName メソッド](iassemblyname-getdisplayname-method.md)|この`IAssemblyName`オブジェクトによって参照されるアセンブリの、人間が判読できる名前を取得します。|  
|[GetName メソッド](iassemblyname-getname-method.md)|この`IAssemblyName`オブジェクトによって参照されるアセンブリの単純な、暗号化されていない名前を取得します。|  
|[GetProperty メソッド](iassemblyname-getproperty-method.md)|指定したによって参照さ`PropertyId`れるプロパティへのポインターを取得します。|  
|[GetVersion メソッド](iassemblyname-getversion-method.md)|この`IAssemblyName`オブジェクトによって参照されるアセンブリのバージョン情報を取得します。|  
|[IsEqual メソッド](iassemblyname-isequal-method.md)|指定した比較`IAssemblyName`フラグに基づいて、 `IAssemblyName`指定したオブジェクトがこのと等しいかどうかを判断します。|  
|[SetProperty メソッド](iassemblyname-setproperty-method.md)|指定したによって参照さ`PropertyId`れるプロパティの値を設定します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Fusion. h  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [Fusion インターフェイス](fusion-interfaces.md)
- [IAssemblyEnum インターフェイス](iassemblyenum-interface.md)
