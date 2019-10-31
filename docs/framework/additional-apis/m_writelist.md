---
title: M_WriteList フィールド
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.Connection.m_WriteList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 235503c1-1d01-4f59-895f-ae2cf15b3345
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9760e301e25bc6e69ab22b563894cb079a8d58bb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120027"
---
# <a name="connectionm_writelist-field"></a>接続. m\_WriteList フィールド

`Connection.m_WriteList` は、HTTP 経由で送信されるようにキューに登録されている <xref:System.Net.HttpWebRequest> オブジェクトの <xref:System.Collections.ArrayList> です。

## <a name="syntax"></a>構文
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> `Connection.m_WriteList` フィールドはプライベートであり、コードで直接使用するためのものではありません。
> 
> Microsoft では、どのような状況でも、実稼働アプリケーションでのこのフィールドの使用はサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.Net>

**アセンブリ:** システム (.dll 内)

**.NET Framework のバージョン:** 2.0 以降で使用できます。
