---
title: SqlStreamChars. Dispose (Boolean) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Dispose
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 44dc97835b8a7141064e8de4d2d5325c40be5a34
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395767"
---
# <a name="sqlstreamcharsdisposeboolean-method"></a>SqlStreamChars. Dispose (Boolean) メソッド

派生クラスでオーバーライドされると、ストリームによって使用されるリソースを解放します。 このメソッドを含むアセンブリには、SQLAccess .dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
protected virtual void Dispose (bool disposing);
```

## <a name="parameters"></a>パラメーター

`disposing`\
マネージド リソースとアンマネージド リソースの両方を解放する場合は `true`。アンマネージド リソースだけを解放する場合は `false`。

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t-0 メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.string (System. Data. .dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
