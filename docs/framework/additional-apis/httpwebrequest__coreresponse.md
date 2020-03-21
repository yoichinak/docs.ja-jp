---
title: _CoreResponse フィールド
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.HttpWebRequest._CoreResponse
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: b275f3eece96ac8a9ae3fb0ebd030c8d79e21fc1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155922"
---
# <a name="httpwebrequest_coreresponse-field"></a>をクリックします。\_コアレスポンスフィールド

`HttpWebRequest._CoreResponse`は、HTTP 応答解析の結果を<xref:System.Exception>含むオブジェクト ([コアレスポンスデータ](coreresponsedata.md)または) です。

## <a name="syntax"></a>構文
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> この API は、コード内で直接使用するためのものではありません。 代わりに、 を<xref:System.Diagnostics.DiagnosticSource>使用してネットワーク コードをフックする必要があります。 [診断ソースユーザーズガイドを](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)参照してください。
>
> マイクロソフトでは、どのような状況でも、運用環境のアプリケーションでこのクラスを使用することはできません。

## <a name="requirements"></a>必要条件

**名前空間:**<xref:System.Net>

**アセンブリ:** システム (システム.dll 内)

**.NET フレームワークのバージョン:** 2.0 以降で利用可能。
