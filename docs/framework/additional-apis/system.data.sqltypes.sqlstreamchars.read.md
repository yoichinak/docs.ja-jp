---
title: SqlStreamChars. Read (Char [], Int32, Int32) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Read
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 9c8a1526e75fdc304022e74a7cc52506762489ea
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395751"
---
# <a name="sqlstreamcharsreadchar-int32-int32-method"></a>SqlStreamChars. Read (Char [], Int32, Int32) メソッド

派生クラスでオーバーライドされると、入力ストリームから次の文字セットを読み取ります。 このメソッドを含むアセンブリには、SQLAccess .dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract int Read (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>パラメーター

`buffer`\
読み取る文字配列。

`offset`\
Origin を基準とするオフセット。

`count`\
現在のストリームから読み取る文字数。

## <a name="returns"></a>戻り値

<xref:System.Int32>\
バッファーに読み取られた合計文字数。

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t-0 メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.string (System. Data. .dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
