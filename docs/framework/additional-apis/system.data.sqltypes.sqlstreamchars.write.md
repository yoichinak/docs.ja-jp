---
title: SqlStreamChars.Write (Char、Int32, Int32) メソッド (System.Data.SqlTypes)
author: stevestein
ms.author: sstein
ms.date: 12/20/2018
ms.technology: dotnet-data
topic_type:
- apiref
api_name:
- System.Data.SqlTypes.SqlStreamChars.Write
api_location:
- System.Data.dll
api_type:
- Assembly
ms.openlocfilehash: 4084c7161eaa91d78eab32f1c14624e0032cdfcf
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675758"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars.Write (Char、Int32, Int32) メソッド

派生クラスでオーバーライドされると、現在のストリームに文字のシーケンスを書き込みし、書き込まれた文字数がこのストリーム内の現在位置を進めます。 このメソッドを含むアセンブリには、SQLAccess.dll で友人関係があります。 SQL Server で使用するものでは。 その他のデータベースには、そのデータベースによって提供されるホスティング メカニズムを使用します。

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>パラメーター

`buffer`  
書き込む文字配列。

`offset`  
原点からのオフセット。

`count`  
現在のストリームに書き込む文字数。

## <a name="remarks"></a>Remarks

> [!WARNING]
> `SqlStreamChars.Write`メソッドはプライベートであり、コード内で直接使用するものではありません。
>
> Microsoft はいかなる運用アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.Data (system.data.dll 内)

**.NET framework のバージョン:** 2.0 以降で使用可能です。
