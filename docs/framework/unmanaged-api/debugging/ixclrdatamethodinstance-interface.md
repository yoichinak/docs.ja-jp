---
title: IXCLRDataMethodInstance インターフェイス
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: f62cbdc4b3e73f0c27492f7ed20b35378654d399
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775503"
---
# <a name="ixclrdatamethodinstance-interface"></a>IXCLRDataMethodInstance インターフェイス

メソッド インスタンスの情報を照会するためのメソッドを提供します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a>メソッド

| メソッド                                                                                                                  | 説明                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [GetILAddressMap](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getiladdressmap-method.md) | アドレスのマッピング情報の IL を取得します。 |
| [GetRepresentativeEntryAddress](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | メソッドのエントリ ポイントは、すべてのネイティブ コンパイルの最も代表的なエントリ ポイントのアドレスを取得します。 |

## <a name="remarks"></a>Remarks

このインターフェイスは、ランタイム内に収めるを任意のヘッダーまたはライブラリ ファイルでは公開されません。 ただし、これは COM インターフェイスから派生した`IUnknown`GUID を持つ`ECD73800-22CA-4b0d-AB55-E9BA7E6318A5`を通常の COM メカニズムを通じて取得できます。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
