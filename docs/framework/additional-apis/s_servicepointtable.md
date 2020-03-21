---
title: フィールドs_ServicePointTable
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155816"
---
# <a name="servicepointmanagers_servicepointtable-field"></a>\_サービスポイントテーブルフィールド

`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable>は、 内のアクティブな HTTP 接続<xref:System.Net.ServicePoint>の一覧を<xref:System.AppDomain>含む ものです。

## <a name="syntax"></a>構文
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> フィールド`ServicePointManager.s_ServicePointTable`はプライベートであり、コード内で直接使用するためのものではありません。
>
> マイクロソフトは、どのような状況においても、本稼動アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
