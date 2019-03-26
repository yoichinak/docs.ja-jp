---
title: Serialization1
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: f0ef8ab378fb3898f2d2e134f0b38668f6794ef3
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409212"
---
# <a name="serialization"></a>シリアル化
シリアル化は、オブジェクトを簡単に永続化または転送できる形式に変換するプロセスです。 たとえば、オブジェクトをシリアル化、HTTP を使用して、移行先のマシンで逆シリアル化された、インターネット経由で転送できます。  
  
 .NET Framework では、さまざまなシリアル化のシナリオ用に最適化された 3 つの主なシリアル化テクノロジを提供します。 これらのテクノロジ、およびテクノロジに関連した主な Framework 型を次の表に示します。  
  
|**テクノロジ名**|**主な種類**|**シナリオ**|  
|-------------------------|--------------------|-------------------|  
|**データ コントラクトのシリアル化**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|永続化全般<br />Web サービス<br />JSON|  
|**XML シリアル化**|<xref:System.Xml.Serialization.XmlSerializer>|XML の構造を完全に制御を持つ XML 形式|  
|**ランタイム シリアル化 (バイナリおよび SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET リモート処理|  
  
 **✓ DO** 新しい型をデザインするときにシリアル化について考えます。  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>サポートする適切なシリアル化テクノロジの選択  
 **✓ CONSIDER** データ コントラクト シリアル化をサポートする場合は、型のインスタンスが永続化または Web サービスで使用する必要があります。  
  
 **✓ CONSIDER** データ コントラクト シリアル化だけでなく、XML のシリアル化をサポートする場合は、型がシリアル化されるときに生成される XML 形式をより細かく制御する必要があります。  
  
 一部を相互運用性、XML を使用する必要があるシナリオの作成でサポートされていないデータ コントラクトのシリアル化、たとえば、XML 属性を生成するために必要な場合があります。  
  
 **✓ CONSIDER** ランタイムのシリアル化をサポートする場合は、型のインスタンスは、.NET リモート処理境界を通過する必要があります。  
  
 **X AVOID** 持続性の一般的な理由についてのみランタイムのシリアル化または XML シリアル化をサポートします。 データ コントラクトのシリアル化を代わりに優先します。  
  
## <a name="supporting-data-contract-serialization"></a>データ コントラクトのシリアル化のサポート  
 型に適用することでデータ コントラクトのシリアル化サポート、<xref:System.Runtime.Serialization.DataContractAttribute>型に、<xref:System.Runtime.Serialization.DataMemberAttribute>型のメンバー (フィールドおよびプロパティ) にします。  
  
 **✓ CONSIDER** 型を部分信頼で使用できる場合、型のパブリック データ メンバーをマークします。  
  
 完全な信頼でデータ コントラクト シリアライザーがシリアル化し、非パブリックな型とメンバーを逆シリアル化がパブリック メンバーのみをシリアル化および部分信頼で逆シリアル化できます。  
  
 **✓ DO** を持つすべてのプロパティの get アクセス操作子および set アクセス操作子を実装する<xref:System.Runtime.Serialization.DataMemberAttribute>です。 データ コントラクト シリアライザーでは、getter と setter のシリアル化可能と見なされる型の両方が必要です。 (.NET Framework 3.5 SP1 では、いくつかのコレクション プロパティできます取得専用。)型を部分信頼で使用しない場合は、1 つまたは両方のプロパティ アクセサーを非パブリックにできます。  
  
 **✓ CONSIDER** 逆シリアル化されたインスタンスを初期化するためにシリアル化コールバックを使用します。  
  
 オブジェクトの逆シリアル化時にはコンストラクターは呼び出されません。 (ルールの例外もあります。 マークされたコレクションのコンス トラクター<xref:System.Runtime.Serialization.CollectionDataContractAttribute>逆シリアル化中に呼び出される)。そのため、通常の構築時に実行されるすべてのロジックは、シリアル化コールバックのいずれかとして実装する必要があります。  
  
 `OnDeserializedAttribute` 最もよく使用されるコールバック属性です。 その他の属性には、<xref:System.Runtime.Serialization.OnDeserializingAttribute>、<xref:System.Runtime.Serialization.OnSerializingAttribute>、および <xref:System.Runtime.Serialization.OnSerializedAttribute> があります。 これらを使用して、逆シリアル化前、シリアル化前、およびシリアル化後に実行されるコールバックをマークすることができます。  
  
 **✓ CONSIDER** を使用して、<xref:System.Runtime.Serialization.KnownTypeAttribute>を複雑なオブジェクト グラフを逆シリアル化時に使用する必要がありますの具象型を示します。  
  
 **✓ DO** 作成またはシリアル化できる型を変更するときに、上位および下位互換性を検討してください。  
  
 シリアル化した型の将来のバージョンは、現在のバージョンの型に逆シリアル化でき、その逆も可能であることを念頭に置いてください。  
  
 データ メンバーもプライベートであり、内部ことはできません変更こと、名前、種類、または型の将来のバージョンでの順序も特別な注意はデータ コントラクト属性に明示的なパラメーターを使用してコントラクトを保持するために実行されない限り、理解しておいてください.  
  
 シリアル化できる型を変更する場合は、シリアル化の互換性をテストします。 新しいバージョンを古いバージョンに逆シリアル化したり、その逆も試してみてください。  
  
 **✓ CONSIDER** 実装<xref:System.Runtime.Serialization.IExtensibleDataObject>種類の異なるバージョン間のラウンド トリップを許可します。  
  
 インターフェイスを使用すると、ラウンドトリッピングの間にデータが失われないようにシリアライザーで確認することができます。 <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType>が現在のバージョンでは、不明な型の将来のバージョンからデータを格納するプロパティを使用し、そのため、データ メンバーに格納されることはできません。 現在のバージョンがシリアル化して、今後のバージョンに逆シリアル化後、追加のデータはシリアル化ストリームに使用できます。  
  
## <a name="supporting-xml-serialization"></a>XML シリアル化のサポート  
 データ コントラクトのシリアル化は、メインの (既定値)、.NET Framework でシリアル化テクノロジがシリアル化のシナリオでデータ コントラクトのシリアル化がサポートされていません。 たとえば、シリアライザーによって作成または使用された XML の形状は完全に制御できません。 そのような微調整が必要な場合は、XML シリアル化は、使用する必要があり、このシリアル化テクノロジをサポートするために、型を設計する必要があります。  
  
 **X AVOID** 生成される XML の構造を制御する非常に強力な理由がない限り、XML シリアル化を具体的には、型を設計します。 このシリアル化テクノロジは、前のセクションで説明したデータ コントラクトのシリアル化よりも優先されます。  
  
 **✓ CONSIDER** を実装する、<xref:System.Xml.Serialization.IXmlSerializable>インターフェイスの XML シリアル化属性を適用することによって提供される内容よりもシリアル化された XML の構造をより詳細に制御する場合。 2 つのメソッド、インターフェイスの<xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A>と<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>を使用するシリアル化された XML ストリームを完全に制御できます。 適用することで、型用に生成される XML スキーマを制御することも、`XmlSchemaProviderAttribute`します。  
  
## <a name="supporting-runtime-serialization"></a>ランタイム シリアル化のサポート  
 ランタイム シリアル化は、.NET リモート処理で使用されるテクノロジです。 .NET リモート処理を使用して、型が転送する場合は、ランタイムのシリアル化をサポートするかどうかを確認する必要があります。  
  
 ランタイム シリアル化の基本的なサポートを適用することで指定することができます、 <xref:System.SerializableAttribute>、しより高度なシナリオでは、単純なランタイム シリアル化可能なパターンを実装する必要があります (実装<xref:System.Runtime.Serialization.ISerializable>シリアル化コンス トラクターを提供)。  
  
 **✓ CONSIDER** 型が .NET リモート処理で使用する場合は、ランタイムのシリアル化をサポートします。 たとえば、<xref:System.AddIn?displayProperty=nameWithType>名前空間は、.NET リモート処理を使用し、すべての型の間で交換`System.AddIn`アドインは、ランタイムのシリアル化をサポートする必要があります。  
  
 **✓ CONSIDER** シリアル化プロセスを完全に制御する場合は、ランタイムのシリアル化可能なパターンを実装します。 たとえば、シリアル化または逆シリアル化されたデータを変換したいとします。  
  
 パターンは単純です。 必要な作業は、<xref:System.Runtime.Serialization.ISerializable> インターフェイスを実装し、オブジェクトを逆シリアル化するときに使用する特別なコンストラクターを指定するだけです。  
  
 **✓ DO** シリアル化コンス トラクターを保護して、型指定された、という名前のサンプルは、ここに示すとおりに正確に 2 つのパラメーターを提供します。  
  
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
  
 **✓ DO** にリンク確認要求を適用<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType>実装します。 これにより、コアとランタイムのシリアライザーがあるメンバーへのアクセスのみ完全に信頼できます。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
