---
title: 接続.m_WriteListフィールド
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
ms.openlocfilehash: 6c60831ddf23ce8ac9afcf244383d24732c3ef8b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155838"
---
# <a name="connectionm_writelist-field"></a>接続.m\_書き込みリスト フィールド

`Connection.m_WriteList`は、HTTP<xref:System.Net.HttpWebRequest>経由で<xref:System.Collections.ArrayList>送信されるキューに入れられます。

## <a name="syntax"></a>構文
  
```csharp  
private ArrayList m_WriteList
```

> [!WARNING]
> フィールド`Connection.m_WriteList`はプライベートであり、コード内で直接使用するためのものではありません。
>
> マイクロソフトは、どのような状況においても、本稼動アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
