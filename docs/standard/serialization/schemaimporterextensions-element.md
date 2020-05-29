---
title: <schemaImporterExtensions> 要素
description: <schemaImporterExtensions> 要素は、XSD の型を .NET Framework の型にマッピングするために XmlSchemaImporter が使用する型を含みます。
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, configuration
- schemaImporterExtensions element
- <schemaImporterExtensions> element
ms.assetid: 465ef2a0-f909-4ac1-9a56-0ead5c849698
ms.openlocfilehash: 5b9820ccdf2c75bed9beda72358c4c4d82ff9ff7
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379788"
---
# <a name="schemaimporterextensions-element"></a>\<schemaImporterExtensions> 要素
XSD の型を .NET Framework の型にマッピングするために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を含みます。 構成ファイルの詳細については、「[構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```xml  
<schemaImporterExtensions>  
    <!-- Add types -->  
</schemaImporterExtensions>  
```  
  
## <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)の \<add> 要素|マッピングを作成するために <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加します。|  
  
## <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)|XML シリアル化を制御する最上位の要素です。|  
  
## <a name="example"></a>例  
 XSD の型を .NET Framework の型にマッピングする際に <xref:System.Xml.Serialization.XmlSchemaImporter> によって使用される型を追加する方法を次のコード例に示します。  
  
```xml  
<system.xml.serialization>  
    <schemaImporterExtensions>  
        <add name = "MobileCapabilities" type =
        "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version - 2.0.0.0, Culture = neutral,
        PublicKeyToken = b03f5f6f11d40a3a" />  
    </schemaImporterExtensions>  
</system.xml.serialization>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)
- [\<schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)の \<add> 要素
- [\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)
