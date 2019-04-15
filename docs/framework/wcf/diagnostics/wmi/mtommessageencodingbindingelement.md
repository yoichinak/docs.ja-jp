---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140479"
---
# <a name="mtommessageencodingbindingelement"></a>MtomMessageEncodingBindingElement
MtomMessageEncodingBindingElement  
  
## <a name="syntax"></a>構文  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a>メソッド  
 MtomMessageEncodingBindingElement クラスで定義されているメソッドはありません。  
  
## <a name="properties"></a>プロパティ  
 MtomMessageEncodingBindingElement クラスには、次のプロパティがあります。  
  
### <a name="encoding"></a>エンコード  
 データ型: string  
  
 アクセスの種類:読み取り専用  
  
 バインディングでメッセージの送信に使用される文字セット エンコーディング。  
  
### <a name="maxreadpoolsize"></a>MaxReadPoolSize  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 新しいリーダーを割り当てずに同時に読み取り可能なメッセージの数を定義する整数です。  
  
### <a name="maxwritepoolsize"></a>MaxWritePoolSize  
 データ型 : sint32  
  
 アクセスの種類:読み取り専用  
  
 新しいライターを割り当てずに同時に送信可能なメッセージの数を定義する整数です。  
  
### <a name="readerquotas"></a>ReaderQuotas  
 データの種類:XmlDictionaryReaderQuotas  
  
 アクセスの種類:読み取り専用  
  
 リーダのクォータ。  
  
## <a name="requirements"></a>必要条件  
  
|MOF|Servicemodel.mof にて宣言済み。|  
|---------|-----------------------------------|  
|名前空間|root\ServiceModel で定義|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>
