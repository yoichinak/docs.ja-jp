---
title: SqlStreamChars.Seek (Int64、SeekOrigin) メソッド (System.Data.SqlTypes)
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
ms.openlocfilehash: 6f802428a73f229e948099788ec21f07efbfab76
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634519"
---
# <a name="sqlstreamcharsseekint64-seekorigin-method"></a>SqlStreamChars.Seek (Int64、SeekOrigin) メソッド

派生クラスでオーバーライドされた場合は、現在のストリーム内の位置を設定します。 このメソッドを含むアセンブリには、SQLAccess.dll で友人関係があります。 SQL Server で使用するものでは。 その他のデータベースには、そのデータベースによって提供されるホスティング メカニズムを使用します。

```csharp
public abstract long Seek (long offset, System.IO.SeekOrigin origin);
```

## <a name="parameters"></a>パラメーター

`offset`\
相対バイト オフセット`origin`します。

`origin`\
新しい位置の取得元となる参照ポイントを示す列挙値の 1 つ。

## <a name="returns"></a>戻り値

<xref:System.Int32>\
現在のストリーム内の新しい位置。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `SqlStreamChars.Seek`メソッドはプライベートであり、コード内で直接使用するものではありません。
>
> Microsoft はいかなる運用アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (system.data.dll 内)

**.NET framework のバージョン:** 2.0 以降で使用可能です。