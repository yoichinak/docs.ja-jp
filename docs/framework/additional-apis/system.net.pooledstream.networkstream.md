---
title: PooledStream. NetworkStream プロパティ (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.PooledStream.NetworkStream
- System.Net.PooledStream.get_NetworkStream
- System.Net.PooledStream.set_NetworkStream
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 541b8c94b30675c1286b48a2291c3bd3e4aeea0b
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847230"
---
# <a name="pooledstreamnetworkstream-property"></a>PooledStream. NetworkStream プロパティ

`PooledStream` ソケットのネットワークストリームを取得または設定します。

## <a name="syntax"></a>構文

```csharp
internal NetworkStream NetworkStream { get; set; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Net.Sockets.NetworkStream>  
`PooledStream` ソケットのネットワークストリーム。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `PooledStream.NetworkStream` プロパティは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (.dll 内)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
