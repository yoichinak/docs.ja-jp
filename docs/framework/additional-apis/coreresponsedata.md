---
title: CoreResponseData クラス
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: 39a14a3df5059cc47cd4879e4d4ba351cc7b655b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79156117"
---
# <a name="coreresponsedata-class"></a>CoreResponseData クラス

この`CoreResponseData`クラスは、HTTP ヘッダーと応答本文の解析を表します。

## <a name="syntax"></a>構文
  
```csharp
internal class CoreResponseData
```

> [!WARNING]
> この API は内部であり、コード内で直接使用するためのものではありません。 代わりに、 を<xref:System.Diagnostics.DiagnosticSource>使用してネットワーク コードをフックする必要があります。 [診断ソースユーザーズガイドを](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)参照してください。
>
> マイクロソフトでは、どのような状況でも、運用環境のアプリケーションでこのクラスを使用することはできません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
