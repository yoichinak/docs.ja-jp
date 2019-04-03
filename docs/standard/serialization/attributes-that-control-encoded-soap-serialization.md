---
title: エンコード済み SOAP シリアル化を制御する属性
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
ms.openlocfilehash: 2961d9abc6c32e78b5a61e8f2bbea5cfcf6677bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547199"
---
# <a name="attributes-that-control-encoded-soap-serialization"></a>エンコード済み SOAP シリアル化を制御する属性

という名前の World Wide Web Consortium (W3C) ドキュメント[簡易オブジェクト アクセス プロトコル (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/) SOAP パラメーターのエンコード方法について説明する省略可能なセクション (セクション 5) が含まれています。 このセクション 5 の仕様に準拠するには、<xref:System.Xml.Serialization> 名前空間で指定されている特殊な属性セットを使用する必要があります。 これらの属性をクラスやクラスのメンバーに適宜適用し、<xref:System.Xml.Serialization.XmlSerializer> を使用して、クラスのインスタンスをシリアル化します。

これらの属性、およびその適用対象と機能を次の表に示します。 詳細については、XML シリアル化を制御するこれらの属性を使用して、[方法。Serialize an Object as SOAP エンコード済み XML Stream](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)と[方法。SOAP エンコード済み XML シリアル化をオーバーライド](how-to-override-encoded-soap-xml-serialization.md)を参照してください。

属性の詳細については、「[属性](../../../docs/standard/attributes/index.md)」を参照してください。

|属性|対象|指定内容|
|---------------|----------------|---------------|
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|クラス メンバーを XML 属性としてシリアル化します。|
|<xref:System.Xml.Serialization.SoapElementAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|クラスを XML 要素としてシリアル化します。|
|<xref:System.Xml.Serialization.SoapEnumAttribute>|列挙体識別子であるパブリック フィールド|列挙体のメンバーの要素名を指定します。|
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|パブリック プロパティとパブリック フィールド|クラスのシリアル化時に、そのクラスに含まれているプロパティまたはフィールドを無視します。|
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|パブリック派生クラス宣言、およびパブリック メソッド (Web サービス記述言語 (WSDL: Web Service Description Language) ドキュメント用)|シリアル化時に認識されるように、スキーマの生成時にその型を対象に含めます。|
|<xref:System.Xml.Serialization.SoapTypeAttribute>|パブリック クラス宣言|クラスを XML 型としてシリアル化します。|

## <a name="see-also"></a>関連項目

- [XML シリアル化および SOAP シリアル化](xml-and-soap-serialization.md)
- [方法: SOAP エンコード済み XML Stream としてオブジェクトをシリアル化します。](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)
- [方法: SOAP エンコード済み XML シリアル化をオーバーライドします。](how-to-override-encoded-soap-xml-serialization.md)
- [属性](../../../docs/standard/attributes/index.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [方法: オブジェクトをシリアル化します。](how-to-serialize-an-object.md)
- [方法: オブジェクトを逆シリアル化します。](how-to-deserialize-an-object.md)
