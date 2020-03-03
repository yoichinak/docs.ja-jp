---
title: XML シリアル化および SOAP シリアル化
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: d9dc68d8e7eced031af404aaec20784573c9930a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62028240"
---
# <a name="xml-and-soap-serialization"></a>XML シリアル化および SOAP シリアル化

XML シリアル化とは、オブジェクトのパブリック フィールドやパブリック プロパティ、またはメソッドのパラメーターや戻り値を、特定の XML スキーマ定義言語 (XSD: XML Schema Definition Language) ドキュメントに準拠する XML ストリームに変換 (シリアル化) する処理です。 XML シリアル化によって、パブリック プロパティおよびパブリック フィールドを含むクラスの型が厳密に指定され、それらのパブリック メンバーは格納または転送できるようにシリアル形式 (この場合は XML) に変換されます。

XML はオープン標準であるため、XML ストリームは、プラットフォームに関係なく、必要に応じて任意のアプリケーションで処理できます。 たとえば、ASP.NET を使用して作成された XML Web サービスは、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、インターネット全体またはイントラネット上の XML Web サービス アプリケーション間でデータを受け渡しする XML ストリームを作成します。 一方、逆シリアル化は、このような XML ストリームからデータを取得して、元のオブジェクトを再構築します。

XML シリアル化を使用して、SOAP 仕様に準拠する XML ストリームにオブジェクトをシリアル化することもできます。 SOAP は、XML を使用してプロシージャ呼び出しを転送するために特別にデザインされた、XML に基づくプロトコルです。

オブジェクトをシリアル化または逆シリアル化するには、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用します。 また、シリアル化する対象のクラスを作成するには、XML スキーマ定義ツールを使用します。

## <a name="in-this-section"></a>このセクションの内容

[XML シリアル化の概要](introducing-xml-serialization.md)  
シリアル化、特に XML シリアル化の一般的な定義を示します。

[方法: オブジェクトをシリアル化します。](how-to-serialize-an-object.md)  
オブジェクトをシリアル化するための詳細な手順について説明します。

[方法: オブジェクトを逆シリアル化します。](how-to-deserialize-an-object.md)  
オブジェクトを逆シリアル化するための詳細な手順について説明します。

[XML シリアル化の例](examples-of-xml-serialization.md)  
XML シリアル化の基本事項を示す例を紹介します。

[XML スキーマ定義ツールと XML シリアル化](the-xml-schema-definition-tool-and-xml-serialization.md)  
XML スキーマ定義ツールを使用して、特定の XML スキーマ定義言語 (XSD) スキーマに準拠するクラスを作成したり、.dll ファイルから XML スキーマを生成したりする方法について説明します。

[属性を使用した XML シリアル化の制御](controlling-xml-serialization-using-attributes.md)  
属性を使用してシリアル化を制御する方法について説明します。

[XML シリアル化を制御する属性](attributes-that-control-xml-serialization.md)  
XML シリアル化の制御に使用する属性を示します。

[方法: XML Stream の代替要素名を指定します。](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
シリアル化のオーバーライドにより、複数の XML ストリームを生成する方法を示す高度なシナリオを紹介します。

[方法: 派生クラスのシリアル化を制御](how-to-control-serialization-of-derived-classes.md)  
派生クラスのシリアル化の制御方法を示す例を紹介します。

[方法: XML 要素および XML 属性の名前を修飾します。](how-to-qualify-xml-element-and-xml-attribute-names.md)  
XML ストリームでの XML 名前空間の使用方法を定義および制御する方法について説明します。

[XML Web サービスを使用した XML シリアル化](xml-serialization-with-xml-web-services.md)  
XML Web サービスでの XML シリアル化の使用方法について説明します。

[方法: SOAP エンコード済み XML Stream としてオブジェクトをシリアル化します。](how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
使用する方法について説明します、 <xref:System.Xml.Serialization.XmlSerializer> World Wide Web Consortium (W3C) ドキュメントのセクション 5 に準拠しているエンコード済みの SOAP XML ストリームを作成するクラス[簡易オブジェクト アクセス プロトコル (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)します。

[方法: SOAP エンコード済み XML シリアル化をオーバーライドします。](how-to-override-encoded-soap-xml-serialization.md)  
SOAP メッセージとしてのオブジェクトの XML シリアル化をオーバーライドするプロセスについて説明します。

[エンコード済み SOAP シリアル化を制御する属性](attributes-that-control-encoded-soap-serialization.md)  
SOAP エンコード済みのシリアル化の制御に使用する属性を示します。

[\<system.xml.serialization> 要素](system-xml-serialization-element.md)  
XML シリアル化を制御する最上位の構成要素です。

[\<dateTimeSerialization> 要素](datetimeserialization-element.md)  
<xref:System.DateTime> オブジェクトのシリアル化モードを制御します。

[\<schemaImporterExtensions> 要素](schemaimporterextensions-element.md)  
<xref:System.Xml.Serialization.XmlSchemaImporter> クラスによって使用される型を含みます。

[\<追加 > 要素の\<schemaImporterExtensions >](add-element-for-schemaimporterextensions.md)  
<xref:System.Xml.Serialization.XmlSchemaImporter> クラスによって使用される型を追加します。

## <a name="related-sections"></a>関連項目

[ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))  
ASP.NET を使用した XML Web サービスのプログラミング方法について説明するトピックを示します。

## <a name="see-also"></a>関連項目

- [バイナリ シリアル化](binary-serialization.md)
