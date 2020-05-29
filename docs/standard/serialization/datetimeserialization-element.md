---
title: <dateTimeSerialization> 要素
description: この記事では、DateTime オブジェクトのシリアル化モードを決定する <dateTimeSerialization> 要素について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- dateTimeSerialization element
- XML serialization, configuration
- <dateTimeSerialization> element
ms.assetid: 90fda55c-7730-41e9-bc4b-6423a4b920af
ms.openlocfilehash: 652a88e25f59cd905e47ef71351e47e67f375286
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/13/2020
ms.locfileid: "83375826"
---
# <a name="datetimeserialization-element"></a>\<dateTimeSerialization> 要素
<xref:System.DateTime> オブジェクトのシリアル化モードを決定します。  
  
 \<configuration>  
\<dateTimeSerialization>  
  
## <a name="syntax"></a>構文  
  
```xml  
<dateTimeSerialization  
    mode = "Roundtrip|Local"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|----------------|-----------------|  
|`mode`|任意。 シリアル化モードを指定します。 <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode> 値のいずれかに設定します。 既定値は **RoundTrip** です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|system.xml.serialization|XML シリアル化を制御する最上位の要素です。|  
  
## <a name="remarks"></a>Remarks  
 .NET Framework の 1.0、1.1、2.0、およびそれ以降のバージョンで、このプロパティが **Local** に設定されている場合、<xref:System.DateTime> オブジェクトは常に現地時刻として書式設定されます。 つまり、ローカル タイム ゾーンの情報が、シリアル化されたデータに必ず組み込まれます。 .NET Framework の以前のバージョンとの互換性を保証するには、このプロパティを **Local** に設定します。  
  
 このプロパティが **Roundtrip** に設定されているバージョン 2.0 以降の .NET Framework では、<xref:System.DateTime> オブジェクトが調べられ、タイム ゾーンがローカル、UTC、または未指定のいずれであるかが特定されます。 その後、この特定された情報を保持する形で、<xref:System.DateTime> オブジェクトがシリアル化されます。 これは既定の動作であり、.NET Framework の以前のバージョンと通信を行わない、すべての新しいアプリケーションで推奨されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.DateTime>
- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [構成ファイル スキーマ](../../../docs/framework/configure-apps/file-schema/index.md)
- [\<schemaImporterExtensions> 要素](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [\<schemaImporterExtensions>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)の \<add> 要素
- [\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)
