---
title: SslState. Sslstate プロパティ (システム .Net. Security)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.Security.SslState.SslProtocol
- System.Net.Security.SslState.get_SslProtocol
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: 6983ac071dad29b240308031ecd0a3562a6856e4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847248"
---
# <a name="sslstatesslprotocol-property"></a>SslState. Sslstate プロパティ

SSL プロトコルのバージョンを取得します。

## <a name="syntax"></a>構文

```csharp
internal SslProtocols SslProtocol { get; }
```

## <a name="property-value"></a>プロパティ値

<xref:System.Security.Authentication.SslProtocols>  
SSL プロトコルのバージョンを指定する列挙値のビットごとの組み合わせ。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `SslState.SslProtocol` プロパティは内部であり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのプロパティの使用はサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Net.Security>

**アセンブリ:** システム (.dll 内)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
