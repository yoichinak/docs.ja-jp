---
title: IXCLRDataProcess インターフェイス
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e7e53615e38d0ab76f9e7c0a753be3c13780057d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178372"
---
# <a name="ixclrdataprocess-interface"></a>IXCLRDataProcess インターフェイス

プロセスに関する情報を照会するためのメソッドを提供します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>メソッド

| Method                                                                                                                                               | 説明                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [GetAppDomainByUniqueId](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | 一意`AppDomain`の ID を使用してプロセス内の を取得します。                                              |
| [StartEnumModules](ixclrdataprocess-startenummodules-method.md)                                   | プロセスのモジュールを列挙するハンドルを提供します。                                        |
| [EnumModule](ixclrdataprocess-enummodule-method.md)                                               | このプロセスのモジュールを列挙します。                                                         |
| [EndEnumModules](ixclrdataprocess-endenummodules-method.md)                                       | モジュールの列挙時に使用される内部反復子によって使用されるリソースを解放します。               |
| [StartEnumMethodInstancesByAddress](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | 指定したアドレス`AppDomain`から開始するメソッド インスタンスを列挙するハンドルを提供します。 |
| [EnumMethodInstanceByAddress](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | アドレス オフセットから開始するこのプロセスのメソッド インスタンスを列挙します。                  |
| [EndEnumMethodInstancesByAddress](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | インスタンスの列挙時に使用される内部反復子によって使用されるリソースを解放します。             |

## <a name="remarks"></a>解説

このインターフェイスはランタイム内に存在し、ヘッダーやライブラリ ファイルを通じて公開されません。 ただし、通常の COM メカニズムを通じて取得`IUnknown`できる`5c552ab6-fc09-4cb3-8e36-22fa03c798b7`GUID から派生する COM インターフェイスです。

## <a name="requirements"></a>必要条件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
