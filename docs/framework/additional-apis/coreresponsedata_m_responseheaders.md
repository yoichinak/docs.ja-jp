---
title: m_ResponseHeaders フィールド
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 723df6dc2de978695608d106e3a01bde286fc4fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156104"
---
# <a name="coreresponsedatam_responseheaders-field"></a>応答\_ヘッダー フィールド

`CoreResponseData.m_ResponseHeaders`は、<xref:System.Net.WebHeaderCollection>サーバー応答に関連付けられたヘッダーの 1 です。

## <a name="syntax"></a>構文
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> この API は、コード内で直接使用するためのものではありません。 代わりに、 を<xref:System.Diagnostics.DiagnosticSource>使用してネットワーク コードをフックする必要があります。 [診断ソースユーザーズガイドを](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)参照してください。
>
> マイクロソフトでは、どのような状況でも、運用環境のアプリケーションでこのクラスを使用することはできません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
