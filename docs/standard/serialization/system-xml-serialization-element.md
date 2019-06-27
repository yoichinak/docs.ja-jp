---
title: <system.xml.serialization> 要素
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 02027a238bc9a2f82963ea841584d2bb3c6446c6
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410544"
---
# <a name="systemxmlserialization-element"></a>\<system.xml.serialization > 要素

XML シリアル化を制御する最上位の要素です。 構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。

\<configuration>
\<system.xml.serialization>

## <a name="syntax"></a>構文

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)|<xref:System.DateTime> オブジェクトのシリアル化モードを決定します。|
|[\<schemaImporterExtensions> 要素](../../../docs/standard/serialization/schemaimporterextensions-element.md)|XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<configuration> 要素](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|

## <a name="example"></a>例

次のコード例は、<xref:System.DateTime> オブジェクトのシリアル化モードを指定し、XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を示します。

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a>関連項目

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<schemaImporterExtensions> 要素](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<追加 > 要素の\<schemaImporterExtensions >](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
