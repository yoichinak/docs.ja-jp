---
title: XML シリアル化を制御する属性
ms.date: 03/30/2017
helpviewer_keywords:
- classes, serializing
- XmlSerializer class, serializing
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
- XML Schema, serializing
ms.assetid: 414b820f-a696-4206-b576-2711d85490c7
ms.openlocfilehash: 0d1aee4650ea29083348af482e445011289e9581
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794967"
---
# <a name="attributes-that-control-xml-serialization"></a>XML シリアル化を制御する属性
次の表に示す属性をクラスおよびクラス メンバーに適用すると、<xref:System.Xml.Serialization.XmlSerializer> がそのクラスのインスタンスをシリアル化または逆シリアル化する方法を制御できます。 これらの属性で XML シリアル化を制御する方法については、「[属性を使用した XML シリアル化の制御](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)」を参照してください。  
  
 また、これらの属性を使用して、XML Web サービスによって生成されるリテラル スタイルの SOAP メッセージを制御することもできます。 これらの属性を XML Web サービス メソッドに適用する方法の詳細については、「[XML Web サービスを使用した XML シリアル化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)」を参照してください。  
  
 属性の詳細については、「[属性](../../../docs/standard/attributes/index.md)」を参照してください。  
  
|属性|対象|指定内容|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.XmlAnyAttributeAttribute>|<xref:System.Xml.XmlAttribute> オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|逆シリアル化時に、スキーマで未定義のすべての XML 属性を表す <xref:System.Xml.XmlAttribute> オブジェクトを配列に挿入します。|  
|<xref:System.Xml.Serialization.XmlAnyElementAttribute>|<xref:System.Xml.XmlElement> オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|逆シリアル化時に、スキーマで未定義のすべての XML 要素を表す <xref:System.Xml.XmlElement> オブジェクトを配列に挿入します。|  
|<xref:System.Xml.Serialization.XmlArrayAttribute>|複合オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|配列のメンバーを XML 配列のメンバーとして生成します。|  
|<xref:System.Xml.Serialization.XmlArrayItemAttribute>|複合オブジェクトの配列を返すパブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|配列に挿入できる派生型を指定します。 通常、<xref:System.Xml.Serialization.XmlArrayAttribute> と共に適用されます。|  
|<xref:System.Xml.Serialization.XmlAttributeAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|メンバーを XML 属性としてシリアル化します。|  
|<xref:System.Xml.Serialization.XmlChoiceIdentifierAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|列挙体を使用して、メンバーを明確に区別できるようにします。|  
|<xref:System.Xml.Serialization.XmlElementAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|フィールドまたはプロパティを XML 要素としてシリアル化します。|  
|<xref:System.Xml.Serialization.XmlEnumAttribute>|列挙体識別子であるパブリック フィールド|列挙体のメンバーの要素名を指定します。|  
|<xref:System.Xml.Serialization.XmlIgnoreAttribute>|パブリック プロパティとパブリック フィールド|クラスのシリアル化時に、そのクラスに含まれているプロパティまたはフィールドを無視します。|  
|<xref:System.Xml.Serialization.XmlIncludeAttribute>|パブリック派生クラス宣言、およびパブリック メソッドの戻り値 (Web サービス記述言語 (WSDL: Web Service Description Language) ドキュメント用)|シリアル化されたときにクラスが認識されるように、スキーマの生成時にそのクラスを対象に含めます。|  
|<xref:System.Xml.Serialization.XmlRootAttribute>|パブリック クラス宣言|属性ターゲットを XML ルート要素として XML シリアル化する方法を制御します。 この属性を使用して、さらに名前空間と要素名を指定できます。|  
|<xref:System.Xml.Serialization.XmlTextAttribute>|パブリック プロパティとパブリック フィールド|プロパティまたはフィールドを XML テキストとしてシリアル化します。|  
|<xref:System.Xml.Serialization.XmlTypeAttribute>|パブリック クラス宣言|XML 型の名前および名前空間を指定します。|  
  
 <xref:System.Xml.Serialization> 名前空間にあるこれらの属性の他に、<xref:System.ComponentModel.DefaultValueAttribute> 属性もフィールドに適用できます。 **DefaultValueAttribute** は、メンバーの値が指定されていない場合に、メンバーに自動的に割り当てられる値を設定します。  
  
 エンコード済みの SOAP XML シリアル化を制御する場合は、「[エンコード済み SOAP シリアル化を制御する属性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML シリアル化および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [属性を使用した XML シリアル化の制御](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [方法: XML Stream の代替要素名を指定します。](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [方法: オブジェクトをシリアル化します。](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [方法: オブジェクトを逆シリアル化します。](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
