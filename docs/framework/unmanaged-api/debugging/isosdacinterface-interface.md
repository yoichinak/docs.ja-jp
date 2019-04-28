---
title: ISOSDacInterface インターフェイス
ms.date: 02/01/2019
api.name:
- ISOSDacInterface Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface Interface
helpviewer.keywords:
- ISOSDacInterface Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ccaf479fc4fb90007b4999e95ee03bdd0529321e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922149"
---
# <a name="isosdacinterface-interface"></a>ISOSDacInterface インターフェイス

データにアクセスするヘルパー メソッドを提供します。`SOS`します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>メソッド

| メソッド                                                                                                               | 説明                                                                                                                   |
| -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| [GetMethodDescData](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescdata-method.md) | 指定した MethodDesc ポインターのデータを取得します。 |
| [GetMethodDescPtrFromIP](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmethoddescptrfromip-method.md) | 指定されたネイティブ命令のアドレスを含むメソッドに対応する MethodDesc ポインターを取得します。 |
| [GetModuleData](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-getmoduledata-method.md)| 指定したアドレスに読み込まれたモジュールに対応するデータをフェッチします。 |

## <a name="remarks"></a>Remarks

このインターフェイスは、ランタイム内に収めるを任意のヘッダーまたはライブラリ ファイルでは公開されません。 ただし、これは COM インターフェイスから派生した`IUnknown`GUID を持つ`436f00f2-b42a-4b9f-870c-e73db66ae930`を通常の COM メカニズムを通じて取得できます。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
