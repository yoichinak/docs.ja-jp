---
title: SqlStreamChars. Write (Char [], Int32, Int32) メソッド (SqlTypes)
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
ms.openlocfilehash: 9d952041122ceb3824712bd81cab7ce4789c9db8
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395585"
---
# <a name="sqlstreamcharswritechar-int32-int32-method"></a>SqlStreamChars. Write (Char [], Int32, Int32) メソッド

派生クラスでオーバーライドされた場合、現在のストリームに文字シーケンスを書き込み、書き込んだ文字数だけストリーム内の現在位置を進めます。 このメソッドを含むアセンブリには、SQLAccess .dll とのフレンド関係があります。 SQL Server での使用を目的としています。 他のデータベースの場合は、そのデータベースによって提供されるホスティングメカニズムを使用します。

```csharp
public abstract void Write (char[] buffer, int offset, int count);
```

## <a name="parameters"></a>パラメーター

`buffer`  
書き込む文字配列。

`offset`  
Origin を基準とするオフセット。

`count`  
現在のストリームに書き込む文字数。

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t-0 メソッドはプライベートであり、コード内で直接使用するためのものではありません。
>
> Microsoft では、この方法を使用した運用アプリケーションの作成をサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Data.SqlTypes>

**アセンブリ:** System.string (System. Data. .dll)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
