---
title: TlsStream. m_Worker フィールド (System.Net)
ms.date: 10/21/2019
ms.technology: dotnet-networking
topic_type:
- apiref
api_name:
- System.Net.TlsStream.m_Worker
api_location:
- System.dll
api_type:
- Assembly
ms.openlocfilehash: d335820d13e1e15e054e824a284615cdbf6c2094
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2019
ms.locfileid: "72847242"
---
# <a name="tlsstreamm_worker-field"></a>TlsStream. m_Worker フィールド

SSL ストリームの状態を表します。

## <a name="syntax"></a>構文

```csharp
private SslState m_Worker;
```

## <a name="field-value"></a>フィールド値

`System.Net.Security.SslState`  
SSL ストリームの状態。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `TlsStream.m_Worker` フィールドはプライベートであり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (.dll 内)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
