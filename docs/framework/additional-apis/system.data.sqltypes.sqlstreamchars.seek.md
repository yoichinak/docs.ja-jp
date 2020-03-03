---
title: SqlStreamChars. Seek (Int64, SeekOrigin) メソッド (SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Seek
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: db8aba0a86c140ba62af8056011226532d415951
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395597"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars. Seek (Int64, SeekOrigin) メソッド

派生クラスでオーバーライドされた場合は、現在のストリーム内の位置を設定します。 このメソッドを含むアセンブリには、SQLAccess .dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>パラメーター

`offset`\
@No__t-0 を基準とするバイトオフセット。

`origin`\
新しい位置を取得する参照ポイントを示す列挙値の1つ。

## <a name="returns"></a>戻り値

<xref:System.Int32>\
現在のストリーム内の新しい位置。

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t-0 メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.string (System. Data. .dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
