---
title: シリアル化とメタデータ
ms.date: 03/30/2017
ms.assetid: 619ecf1c-1ca5-4d66-8934-62fe7aad78c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 937577f86ec854f5a458fe6067836a85a540695a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913802"
---
# <a name="serialization-and-metadata"></a>シリアル化とメタデータ

アプリでオブジェクトをシリアル化および逆シリアル化する場合、ランタイム ディレクティブ (.rd.xml) ファイルにエントリを追加して、必要なメタデータが実行時に確実に存在するようにする必要があることがあります。 シリアライザーには次の 2 つのカテゴリがあり、それぞれランタイム ディレクティブ ファイルで異なる処理が必要です。  
  
- リフレクション ベースのサードパーティ シリアライザー。 この場合、ランタイム ディレクティブ ファイルの変更が必要です。詳細については次のセクションで説明します。  
  
- .NET Framework クラス ライブラリにある非リフレクション ベースのシリアライザー。 この場合、ランタイム ディレクティブ ファイルの変更が必要なことがあります。詳細については、「[Microsoft のシリアライザー](#Microsoft)」セクションで説明します。  
  
<a name="ThirdParty"></a>
## <a name="third-party-serializers"></a>サードパーティ シリアライザー

 Newtonsoft.JSON などのサードパーティ シリアライザーは通常リフレクション ベースです。 シリアル化データのバイナリ ラージ オブジェクト (BLOB) の場合、対象の型のフィールドを名前で検索することで、データ内のフィールドが具象型に割り当てられます。 少なくとも、これらのライブラリを使用すると、`List<Type>` コレクションでシリアル化または逆シリアル化しようとする <xref:System.Type> オブジェクトごとに [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外が発生します。  
  
 これらのシリアライザーでメタデータの欠落により引き起こされる問題に対処する最も簡単な方法は、1 つの名前空間 (`App.Models` など) でシリアル化に使用される型を収集し、`Serialize` メタデータ ディレクティブを適用することです。  
  
```xml  
<Namespace Name="App.Models" Serialize="Required PublicAndInternal" />  
```  
  
 この例で使用されている構文の詳細については、「[\<Namespace> 要素](../../../docs/framework/net-native/namespace-element-net-native.md)」を参照してください。  
  
<a name="Microsoft"></a>
## <a name="microsoft-serializers"></a>Microsoft のシリアライザー

 <xref:System.Runtime.Serialization.DataContractSerializer>、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>、および <xref:System.Xml.Serialization.XmlSerializer> クラスではリフレクションを利用しませんが、シリアル化または逆シリアル化されるオブジェクトに基づいてコードが生成される必要があります。 各シリアライザーのオーバーロードされたコンストラクターには、シリアル化または逆シリアル化される型を指定する <xref:System.Type> パラメーターが含まれます。 次の 2 つのセクションで説明するように、コードでのその型の指定方法によってユーザーが実行する必要のあるアクションが定義されます。  
  
### <a name="typeof-used-in-the-constructor"></a>コンストラクターで使用される typeof

 これらのシリアル化クラスのコンストラクターを呼び出し、メソッド呼び出しC#に[typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator)演算子を含めると、**追加の作業を行う必要はありません**。 たとえば、シリアル化クラス コンストラクターに対する次の各呼び出しでは、`typeof` キーワードがコンストラクターに渡される式の一部として使用されます。  
  
 [!code-csharp[ProjectN#5](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#5)]  
  
 このコードは、.NET ネイティブコンパイラによって自動的に処理されます。  
  
### <a name="typeof-used-outside-the-constructor"></a>コンストラクターの外部で使用される typeof

 次のコードのように、これらのシリアル化クラスC#のコンストラクターを呼び出し、コンストラクターの<xref:System.Type>パラメーターに指定された式の外側で[typeof](../../csharp/language-reference/operators/type-testing-and-cast.md#typeof-operator)演算子を使用した場合、.NET ネイティブコンパイラは型を解決できません。  
  
 [!code-csharp[ProjectN#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#6)]  
  
 この場合は、次のようなエントリを追加して、ランタイム ディレクティブ ファイルで型を指定する必要があります。  
  
```xml  
<Type Name="DataSet" Browse="Required Public" />  
```  
  
 同様に、のような<xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>コンストラクターを呼び出し、次のコードのように、シリアル化する追加<xref:System.Type>のオブジェクトの配列を指定すると、.NET ネイティブコンパイラはこれらの型を解決できません。  
  
 [!code-csharp[ProjectN#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/serialize1.cs#7)]  
  
 型ごとに次のようなエントリをランタイム ディレクティブ ファイルに追加する必要があります。  
  
```xml  
<Type Name="t" Browse="Required Public" />  
```  
  
 この例で使用されている構文の詳細については、「[\<Type> 要素](../../../docs/framework/net-native/type-element-net-native.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)
- [\<> 要素を入力します](../../../docs/framework/net-native/type-element-net-native.md)
- [\<Namespace > 要素](../../../docs/framework/net-native/namespace-element-net-native.md)
