---
title: HttpWebRequest._CoreResponse フィールド
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
ms.openlocfilehash: 3627c9bf0d72ccec3a0d6d9c7c89b62f83dcd4b4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706066"
---
# <a name="httpwebrequestcoreresponse-field"></a>HttpWebRequest します。\_CoreResponse フィールド

`HttpWebRequest._CoreResponse` オブジェクトは、(いずれかを[CoreResponseData](coreresponsedata.md)または<xref:System.Exception>) HTTP 応答の解析の結果を格納します。

## <a name="syntax"></a>構文
  
```csharp
private object _CoreResponse
```

> [!WARNING]
> この API は、コード内で直接使用するものではありません。 代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。 参照してください[DiagnosticSource ユーザー ガイド](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)します。
> 
> Microsoft はいかなる運用アプリケーションでこのクラスの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Net>

**アセンブリ:**(System.dll) のシステム

**.NET framework のバージョン:** 2.0 以降で使用可能です。
