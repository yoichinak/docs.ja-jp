---
title: シリアル化
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: 0259bf82e74cbca7df8da246ca2e6ba7ef4542b3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868525"
---
# <a name="serialization"></a>シリアル化
シリアル化は、オブジェクトを、簡単に永続化または転送できる形式に変換するプロセスです。 たとえば、オブジェクトをシリアル化し、HTTP を使用してインターネット経由で転送し、ターゲットコンピューターで逆シリアル化することができます。  
  
 .NET Framework には、さまざまなシリアル化シナリオ用に最適化された3つの主要なシリアル化テクノロジがあります。 これらのテクノロジ、およびテクノロジに関連した主な Framework 型を次の表に示します。  
  
|**テクノロジ名**|**主要な型**|**シナリオ**|  
|-------------------------|--------------------|-------------------|  
|**データコントラクトのシリアル化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|永続化全般<br />Web サービス<br />JSON|  
|**XML シリアル化**|<xref:System.Xml.Serialization.XmlSerializer>|Xml の構造を完全に制御する XML 形式|  
|**ランタイムのシリアル化 (バイナリおよび SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET リモート処理|  
  
 **✓ DO** 新しい型をデザインするときにシリアル化について考えます。  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>サポートする適切なシリアル化テクノロジの選択  
 **✓ CONSIDER** データ コントラクト シリアル化をサポートする場合は、型のインスタンスが永続化または Web サービスで使用する必要があります。  
  
 **✓ CONSIDER** データ コントラクト シリアル化だけでなく、XML のシリアル化をサポートする場合は、型がシリアル化されるときに生成される XML 形式をより細かく制御する必要があります。  
  
 これは、データコントラクトのシリアル化でサポートされていない XML コンストラクトを使用する必要がある場合 (XML 属性を生成する場合など) に必要になることがあります。  
  
 **✓ CONSIDER** ランタイムのシリアル化をサポートする場合は、型のインスタンスは、.NET リモート処理境界を通過する必要があります。  
  
 **X AVOID** 持続性の一般的な理由についてのみランタイムのシリアル化または XML シリアル化をサポートします。 代わりに、データコントラクトのシリアル化を優先します。  
  
## <a name="supporting-data-contract-serialization"></a>データ コントラクトのシリアル化のサポート  
 型<xref:System.Runtime.Serialization.DataContractAttribute> に<xref:System.Runtime.Serialization.DataMemberAttribute>を適用することにより、型のメンバー (フィールドおよびプロパティ) にを適用することで、データコントラクトのシリアル化をサポートできます。  
  
 **✓ CONSIDER** 型を部分信頼で使用できる場合、型のパブリック データ メンバーをマークします。  
  
 完全信頼では、データコントラクトシリアライザーは、非パブリックな型とメンバーをシリアル化および逆シリアル化できますが、部分信頼でシリアル化および逆シリアル化できるのはパブリックメンバーだけです。  
  
 **✓ DO** を持つすべてのプロパティの get アクセス操作子および set アクセス操作子を実装する<xref:System.Runtime.Serialization.DataMemberAttribute>です。 データコントラクトシリアライザーでは、型の getter と setter の両方がシリアル化可能と見なされる必要があります。 (.NET Framework 3.5 SP1 では、一部のコレクションプロパティを取得専用にすることができます)。型を部分信頼で使用しない場合は、1 つまたは両方のプロパティ アクセサーを非パブリックにできます。  
  
 **✓ CONSIDER** 逆シリアル化されたインスタンスを初期化するためにシリアル化コールバックを使用します。  
  
 オブジェクトの逆シリアル化時にはコンストラクターは呼び出されません。 (規則には例外があります。 でマークされた<xref:System.Runtime.Serialization.CollectionDataContractAttribute>コレクションのコンストラクターは、逆シリアル化中に呼び出されます。)したがって、通常の構築時に実行されるすべてのロジックは、シリアル化コールバックの1つとして実装する必要があります。  
  
 `OnDeserializedAttribute`最もよく使用されるコールバック属性です。 その他の属性には、<xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute>、および <xref:System.Runtime.Serialization.OnSerializedAttribute> があります。 これらを使用して、逆シリアル化前、シリアル化前、およびシリアル化後に実行されるコールバックをマークすることができます。  
  
 **✓ CONSIDER** を使用して、<xref:System.Runtime.Serialization.KnownTypeAttribute>を複雑なオブジェクト グラフを逆シリアル化時に使用する必要がありますの具象型を示します。  
  
 **✓ DO** 作成またはシリアル化できる型を変更するときに、上位および下位互換性を検討してください。  
  
 シリアル化した型の将来のバージョンは、現在のバージョンの型に逆シリアル化でき、その逆も可能であることを念頭に置いてください。  
  
 データコントラクト属性への明示的なパラメーターを使用してコントラクトを保持する特別な注意を払う場合を除き、データメンバー (プライベートおよび内部でも) では、将来のバージョンでも、名前、型、および順序を変更することはできないことを理解してください.  
  
 シリアル化可能な型に変更を加えるときに、シリアル化の互換性をテストします。 新しいバージョンを古いバージョンに逆シリアル化したり、その逆も試してみてください。  
  
 **✓ CONSIDER** 実装<xref:System.Runtime.Serialization.IExtensibleDataObject>種類の異なるバージョン間のラウンド トリップを許可します。  
  
 インターフェイスを使用すると、ラウンドトリッピングの間にデータが失われないようにシリアライザーで確認することができます。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>プロパティは、現在のバージョンでは不明な型の将来のバージョンからデータを格納するために使用されます。そのため、データメンバーに格納することはできません。 現在のバージョンを後でシリアル化および逆シリアル化した後に、シリアル化されたストリームで使用できるようになります。  
  
## <a name="supporting-xml-serialization"></a>XML シリアル化のサポート  
 データコントラクトのシリアル化は .NET Framework の主要な (既定の) シリアル化テクノロジですが、データコントラクトのシリアル化でサポートされていないシリアル化のシナリオがあります。 たとえば、シリアライザーによって作成または使用された XML の形状は完全に制御できません。 このような細かい制御が必要な場合は、XML シリアル化を使用する必要があり、このシリアル化テクノロジをサポートするために型をデザインする必要があります。  
  
 **X AVOID** 生成される XML の構造を制御する非常に強力な理由がない限り、XML シリアル化を具体的には、型を設計します。 このシリアル化テクノロジは、前のセクションで説明したデータ コントラクトのシリアル化よりも優先されます。  
  
 **✓ CONSIDER** を実装する、<xref:System.Xml.Serialization.IXmlSerializable>インターフェイスの XML シリアル化属性を適用することによって提供される内容よりもシリアル化された XML の構造をより詳細に制御する場合。 インターフェイスの2つのメソッド<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>で<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>あるとを使用すると、シリアル化された XML ストリームを完全に制御できます。 を適用`XmlSchemaProviderAttribute`して、型に対して生成される XML スキーマを制御することもできます。  
  
## <a name="supporting-runtime-serialization"></a>ランタイム シリアル化のサポート  
 ランタイムシリアル化は、.NET リモート処理で使用されるテクノロジです。 .NET リモート処理を使用して型が転送されると思われる場合は、ランタイムシリアル化をサポートしていることを確認する必要があります。  
  
 ランタイムシリアル化の基本的なサポートは、 <xref:System.SerializableAttribute>を適用することによって実現できます。また、より高度なシナリオでは、単純なランタイムシリアル化可能パターンの実装 (シリアル化コンストラクターの実装<xref:System.Runtime.Serialization.ISerializable>と提供) が必要になります。  
  
 **✓ CONSIDER** 型が .NET リモート処理で使用する場合は、ランタイムのシリアル化をサポートします。 たとえば、名前空間<xref:System.AddIn?displayProperty=nameWithType>は .net リモート処理を使用するため、アドイン間`System.AddIn`で交換されるすべての型でランタイムシリアル化をサポートする必要があります。  
  
 **✓ CONSIDER** シリアル化プロセスを完全に制御する場合は、ランタイムのシリアル化可能なパターンを実装します。 たとえば、シリアル化または逆シリアル化されたデータを変換したいとします。  
  
 パターンは単純です。 必要な作業は、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装し、オブジェクトを逆シリアル化するときに使用する特別なコンストラクターを指定するだけです。  
  
 **✓ DO** シリアル化コンストラクターを保護して、型指定された、という名前のサンプルは、ここに示すとおりに正確に 2 つのパラメーターを提供します。  
  
```csharp
[Serializable]  
public class Person : ISerializable
{  
    protected Person(SerializationInfo info, StreamingContext context)
    {  
        // ...  
    }  
}  
```
  
 **✓ DO** 実装、<xref:System.Runtime.Serialization.ISerializable>メンバー明示的にします。  
  
 **✓ DO** にリンク確認要求を適用<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>実装します。 これにより、完全に信頼されたコアとランタイムシリアライザーだけがメンバーにアクセスできるようになります。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *次のフレームワークの設計ガイドラインから[、ピアソン教育, inc. のアクセス許可によって再度ご説明します。Microsoft Windows 開発シリーズの一部として、Addison-Wesley](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Professional によって2008年10月22日公開された、再利用可能な .net ライブラリの Krzysztof Cwalina および Brad abrams の規則、表現、パターン。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
