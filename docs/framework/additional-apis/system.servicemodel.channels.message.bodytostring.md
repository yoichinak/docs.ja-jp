---
title: Message.BodyToString Method (System.ServiceModel.Channels)
author: mairaw
ms.author: mairaw
ms.date: 11/01/2019
topic_type:
- apiref
api_name:
- System.ServiceModel.Channels.Message.BodyToString
api_location:
- system.servicemodel.dll
api_type:
- Assembly
ms.openlocfilehash: 7b0b56bfda1c0c37f43f95e9684d3b4042c1b97c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451312"
---
# <a name="messagebodytostring-method"></a>Message.BodyToString Method

Converts the message body into a string by calling the <xref:System.ServiceModel.Channels.Message.OnBodyToString%2A?displayProperty=nameWithType> method.

```csharp
internal void BodyToString(XmlDictionaryWriter writer);
```

## <a name="parameters"></a>パラメーター

- `writer` <xref:System.Xml.XmlDictionaryWriter>\
  The writer that is used to convert the message body to a string.

## <a name="remarks"></a>Remarks

> [!WARNING]
> The `Message.BodyToString` method is internal and is not meant to be used directly in your code.
>
> Microsoft does not support the use of this method in a production application under any circumstance.

## <a name="requirements"></a>［要件］

**名前空間:** <xref:System.ServiceModel.Channels>

**Assembly:** System.ServiceModel.dll

**.NET Framework versions:** Available since 3.0.
