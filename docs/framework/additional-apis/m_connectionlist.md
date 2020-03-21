---
title: 接続グループ.m_ConnectionList フィールド
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ConnectionGroup.m_ConnectionList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 186083cf-8dff-4600-a2ab-6fed4b4de6af
ms.openlocfilehash: 8eb6f215c36e214f7095eeba90bf0aed66dfcea0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155851"
---
# <a name="connectiongroupm_connectionlist-field"></a>接続グループ.m\_接続リスト フィールド

`ConnectionGroup.m_ConnectionList`は、<xref:System.Collections.ArrayList>同じ URI を提供し、有効期限や認証などの他のプロパティで同じ値を共有する接続オブジェクトの 1 つです。

## <a name="syntax"></a>構文
  
```csharp  
private ArrayList m_ConnectionList
```

> [!WARNING]
> フィールド`ConnectionGroup.m_ConnectionList`はプライベートであり、コード内で直接使用するためのものではありません。
>
> マイクロソフトは、どのような状況においても、本稼動アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
