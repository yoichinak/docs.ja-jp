---
title: スキーマのインポートとエクスポート
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractExporter class
- XsdDataContractImporter class
ms.assetid: 0da32b50-ccd9-463a-844c-7fe803d3bf44
ms.openlocfilehash: a14ee9e5916133be3979650055cf3e57899a4cca
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591801"
---
# <a name="schema-import-and-export"></a>スキーマのインポートとエクスポート
Windows Communication Foundation (WCF) には、新しいシリアル化エンジンが含まれています、<xref:System.Runtime.Serialization.DataContractSerializer>します。 `DataContractSerializer`双方向) の「.NET Framework のオブジェクトと XML に変換します。 シリアライザー自体だけでなく WCF には、関連付けられているスキーマのインポートとスキーマ エクスポート機構が含まれています。 *スキーマ*は、シリアライザーが生成する、またはデシリアライザーがアクセスできる、XML の構造の正式かつ正確であり、コンピューターが判読できる説明です。 WCF では、スキーマ表現として、これは広く、多数のサードパーティ プラットフォームと相互運用可能な World Wide Web Consortium (W3C) XML スキーマ定義言語 (XSD) を使用します。  
  
 スキーマ インポート コンポーネント<xref:System.Runtime.Serialization.XsdDataContractImporter>XSD スキーマ ドキュメントを受け取り、生成、シリアル化されたフォームが指定されたスキーマに対応できるように、.NET Framework のクラス (通常のデータ コントラクト クラス)。  
  
 たとえば、次のスキーマ フラグメントがあるとします。  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
 これは、読みやすいように、やや簡素化された次の型を生成します。  
  
 [!code-csharp[c_SchemaImportExport#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#1)]
 [!code-vb[c_SchemaImportExport#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#1)]  
  
 生成された型がいくつかのデータ コントラクトのベスト プラクティスに従うことに注意してください (ある[ベスト プラクティス。データ コントラクトのバージョン管理](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md))。  
  
- この型は <xref:System.Runtime.Serialization.IExtensibleDataObject> インターフェイスを実装します。 詳細については、「[上位互換性のあるデータ コントラクト](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)」を参照してください。  
  
- データ メンバーは、プライベート フィールドをラップするパブリック プロパティとして実装されます。  
  
- クラスは部分クラスであり、生成されたコードを変更せずに追加を行うことができます。  
  
 <xref:System.Runtime.Serialization.XsdDataContractExporter> では反転を実行できます。つまり、`DataContractSerializer` によってシリアル化できる型を受け取って XSD スキーマ ドキュメントを生成できます。  
  
## <a name="fidelity-is-not-guaranteed"></a>忠実性は保証されない  
 スキーマや型のラウンド トリップでの完全な忠実性は保証されません  (A*ラウンド トリップ*クラスのセットを作成し、もう一度スキーマを作成する結果をエクスポートするスキーマをインポートすることを意味します)。同じスキーマが返されない場合があります。 また、これとは逆のプロセスでも忠実性は保証されません  (スキーマを生成する型をエクスポートしてから、型をインポートし直す場合です。 この場合も、同じ型が返されない可能性があります)。  
  
## <a name="supported-types"></a>サポートされている型  
 データ コントラクト モデルは、WC3 スキーマの限られたサブセットしかサポートしません。 このサブセットに準拠しないスキーマを使用すると、インポート プロセスで例外が発生します。 たとえば、データ コントラクトのデータ メンバーを XML 属性としてシリアル化するように指定することはできません。 したがって、XML 属性を使用する必要があるスキーマはサポートされず、適切な XML 投影を持つデータ コントラクトを生成できないため、インポート時に例外が発生します。  
  
 たとえば、次のスキーマ フラグメントは、既定のインポート設定を使用してインポートすることはできません。  
  
 [!code-xml[c_SchemaImportExport#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#9)]  
  
 詳細については、次を参照してください。 [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)します。 スキーマがデータ コントラクト ルールに準拠していない場合は、別のシリアル化エンジンを使用します。 たとえば、<xref:System.Xml.Serialization.XmlSerializer> は、独自のスキーマ インポート機構を使用します。 また、サポートされるスキーマの範囲を拡張する特別なインポート モードもあります。 詳細については、生成に関するセクションを参照してください。<xref:System.Xml.Serialization.IXmlSerializable>型[クラスを生成するスキーマをインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)します。  
  
 `XsdDataContractExporter`でシリアル化できる .NET Framework の型をサポートしている、`DataContractSerializer`します。 詳細については、次を参照してください。[型は、データ コントラクト シリアライザーでサポートされている](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)します。 通常、`XsdDataContractExporter` を使用して作成されたスキーマは、`XsdDataContractImporter` を使用してカスタマイズしない限り、<xref:System.Xml.Serialization.XmlSchemaProviderAttribute> で使用できる有効なデータです。  
  
 使用しての詳細については、<xref:System.Runtime.Serialization.XsdDataContractImporter>を参照してください[クラスを生成するスキーマをインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)します。  
  
 使用しての詳細については、<xref:System.Runtime.Serialization.XsdDataContractExporter>を参照してください[クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- [クラスを作成するためのスキーマのインポート](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)
- [クラスからのスキーマのエクスポート](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
