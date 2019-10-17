---
title: PrepForRemoting メソッド (System)
author: mairaw
ms.author: mairaw
ms.date: 10/08/2019
topic_type:
- apiref
api_name:
- System.Exception.PrepForRemoting
api_location:
- mscorlib.dll
api_type:
- Assembly
ms.openlocfilehash: 057390d64f70d3cb8eba7d4b29b94570fdca77e3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72405898"
---
# <a name="exceptionprepforremoting-method"></a>PrepForRemoting メソッド

クライアント呼び出しサイトで例外が再スローされる前に、サーバー側スタックトレースをメッセージに追加して保存します。

```csharp
internal Exception PrepForRemoting();
```

## <a name="returns"></a>戻り値

<xref:System.Exception>  
この <xref:System.Exception> インスタンス。

## <a name="remarks"></a>Remarks

> [!WARNING]
> @No__t-0 メソッドは内部にあり、コードで直接使用するためのものではありません。
>
> Microsoft では、どのような状況でも、実稼働アプリケーションでこの方法を使用することはサポートしていません。

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System>

**アセンブリ:** mscorlib.dll (mscorlib.dll 内)

**.NET Framework のバージョン:** 1.0 以降で使用できます。
