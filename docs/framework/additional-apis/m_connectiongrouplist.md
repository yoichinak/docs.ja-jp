---
title: サービスポイント.m_ConnectionGroupListフィールド
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: 2b1b46085ed035b67fd01447727b406fe3895980
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155896"
---
# <a name="servicepointm_connectiongrouplist-field"></a>\_接続グループ リスト フィールド

`ServicePoint.m_ConnectionGroupList`は接続<xref:System.Collections.Hashtable>グループの 1 で、それぞれが 's URI の接続を<xref:System.Net.ServicePoint>保持しています。

## <a name="syntax"></a>構文
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> フィールド`ServicePoint.m_ConnectionGroupList`はプライベートであり、コード内で直接使用するためのものではありません。
>
> マイクロソフトは、どのような状況においても、本稼動アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
