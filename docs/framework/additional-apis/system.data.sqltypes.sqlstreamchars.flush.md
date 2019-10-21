---
title: SqlStreamChars. Flush メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Flush
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 38ade5ce38cfe5003b2d06c0d8bb2db1a20bc05b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395623"
---
# <a name="sqlstreamcharsflush-method"></a>SqlStreamChars. Flush メソッド

派生クラスによってオーバーライドされた場合は、ストリームに対応するすべてのバッファーをクリアし、バッファー内のデータを基になるデバイスに書き込みます。 このメソッドを含むアセンブリには、SQLAccess .dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

## <a name="syntax"></a>構文

```csharp
public abstract void Flush ();
```

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t-0 メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.string (System. Data. .dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
