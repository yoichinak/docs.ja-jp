---
title: ServicePoint. m_ConnectionGroupList フィールド
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1991dae4d03f617857b860f920077531f7937bf1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120055"
---
# <a name="servicepointm_connectiongrouplist-field"></a>ServicePoint. m\_ConnectionGroupList フィールド

`ServicePoint.m_ConnectionGroupList` は、それぞれ <xref:System.Net.ServicePoint>の URI の接続を保持する接続グループの <xref:System.Collections.Hashtable> です。

## <a name="syntax"></a>構文
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> `ServicePoint.m_ConnectionGroupList` フィールドはプライベートであり、コードで直接使用するためのものではありません。
> 
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (.dll 内)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
