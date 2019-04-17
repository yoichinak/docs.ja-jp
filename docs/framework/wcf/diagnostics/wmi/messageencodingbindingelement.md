---
title: MessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 7f750742-b96b-498f-bf5e-05933a1a5961
ms.openlocfilehash: f7af547148acacfb83d4e41aa1a085e3eabaafdc
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2019
ms.locfileid: "59610848"
---
# <a name="messageencodingbindingelement"></a>MessageEncodingBindingElement

MessageEncodingBindingElement

## <a name="syntax"></a>構文

```csharp
class MessageEncodingBindingElement : BindingElement
{
    string MessageVersion;
};
```

## <a name="methods"></a>メソッド

MessageEncodingBindingElement クラスは、メソッドを一切定義しません。

## <a name="properties"></a>プロパティ

MessageEncodingBindingElement クラスには、次のプロパティがあります。

### <a name="messageversion"></a>MessageVersion

データ型: string

アクセスの種類:読み取り専用

バインディングを使用して送信されたメッセージの SOAP バージョン。

## <a name="requirements"></a>必要条件

|MOF|Servicemodel.mof にて宣言済み。|
|---------|-----------------------------------|
|名前空間|root\ServiceModel で定義|

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>
