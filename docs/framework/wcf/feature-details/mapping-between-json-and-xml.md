---
title: JSON と XML 間のマッピング
ms.date: 03/30/2017
ms.assetid: 22ee1f52-c708-4024-bbf0-572e0dae64af
ms.openlocfilehash: ef5eaac8fc75149ac518ce322808a84bbab5506b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636434"
---
# <a name="mapping-between-json-and-xml"></a>JSON と XML 間のマッピング
<xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory> によって作成されるリーダーとライターには、JSON (JavaScript Object Notation) コンテンツでの XML API が備わっています。 JSON は、JavaScript のオブジェクト リテラルのサブセットを使用してデータをエンコードします。 リーダーとライターはこのファクトリによって生成された、ときにも使用 JSON コンテンツの送信または受信を使用する Windows Communication Foundation (WCF) アプリケーション、<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>または<xref:System.ServiceModel.WebHttpBinding>します。

JSON リーダーは JSON コンテンツで初期化されると、XML インスタンスで動作するテキストの XML リーダーと同じ方法で動作します。 テキストの XML リーダーでの一連の呼び出しによって特定の XML インスタンスが生成されると、JSON ライターは JSON コンテンツを書き出します。 このトピックでは、高度なシナリオで使用するために、この XML のインスタンスと JSON コンテンツ間のマッピングについて説明します。

内部的には、JSON は、WCF によって処理されると、XML infoset として表されます。 通常、マッピングは論理上、この内部表現を考慮する必要はありません。JSON は通常は物理的にメモリ内 XML に変換または XML から JSON に変換します。 マッピングとは、XML API を使用して JSON コンテンツにアクセスすることを意味します。

WCF では、JSON を使用する場合、通常のシナリオは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>によって自動的に接続されて、<xref:System.ServiceModel.Description.WebScriptEnablingBehavior>動作、または、<xref:System.ServiceModel.Description.WebHttpBehavior>該当する場合。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> は、JSON と XML 情報セット間のマッピングを認識し、直接 JSON を処理しているかのように動作します。 XML が次のマッピングに従うという了解の下に、任意の XML リーダーまたはライターで <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用できます。

高度なシナリオでは、次のマッピングへの直接アクセスが必要になることがあります。 このようなシナリオが生じるのは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> に依存することなく、独自の方法で JSON のシリアル化および逆シリアル化を行うとき、または JSON を含むメッセージに対して直接 <xref:System.ServiceModel.Channels.Message> 型を処理するときです。 JSON と XML 間のマッピングは、メッセージ ログにも使用されます。 メッセージ ログ機能を使用して、WCF では、JSON メッセージは、次のセクションで説明するマッピングに従って XML として記録されます。

マッピングの概念を明確にするために、次に JSON ドキュメントの例を示します。

```json
{"product":"pencil","price":12}
```

前述のリーダーのいずれか 1 つを使用してこの JSON ドキュメントを読み取るには、次の XML ドキュメントの読み取りに使用するシーケンスと同一の、<xref:System.Xml.XmlDictionaryReader> 呼び出しのシーケンスを使用します。

```xml
<root type="object">
    <product type="string">pencil</product>
    <price type="number">12</price>
</root>
```

さらに、JSON メッセージの例では、WCF によって受信され、ログに記録が場合、先行ログの XML フラグメントが表示されます。

## <a name="mapping-between-json-and-the-xml-infoset"></a>JSON と XML 情報セット間のマッピング
」の説明に従っての JSON の間のマッピングが正式は[RFC 4627](https://go.microsoft.com/fwlink/?LinkId=98808) (を除く特定と緩和された特定の制限を追加するその他の制限) XML 情報セット (としないテキスト形式の XML) として記載[XML 情報設定](https://go.microsoft.com/fwlink/?LinkId=98809)します。 定義は、このトピックを参照してください。*情報項目*と角かっこ [] 内のフィールド。

空白の JSON ドキュメントが空の XML ドキュメントにマップされ、空の XML ドキュメントは空白の JSON ドキュメントにマップされます。 XML JSON へのマッピングからでは、空白文字の前とドキュメントの後に末尾の空白文字は使用できません。

マッピングは、ドキュメント情報項目 (DII: Document Information Item) または要素情報項目 (EII: Element Information Item) のいずれか一方と JSON の間に定義されます。 EII、または DII の [document element] プロパティは、Root JSON Element と呼ばれます。 また、ドキュメント フラグメント (ルート要素を複数持つ XML) は、このマッピングではサポートされません。

例:次のドキュメント:

```xml
<?xml version="1.0"?>
<root type="number">42</root>`
```

また、次の要素があるとします。

```xml
<root type="number">42</root>
```

どちらにも JSON へのマッピングが存在します。 <`root`> 要素がどちらの場合も、Root JSON Element です。

また、DII の場合は次の点を考慮する必要があります。

- [children] 一覧には、除外する必要のある項目が含まれています。 JSON からマッピングされた XML を読み取るときは、この事実に依存しないでください。

- [children] 一覧には、注釈情報項目が保持されません。

- [children] 一覧には、DTD 情報項目が保持されません。

- [Children] 一覧は個人情報 (PI) の情報項目が保持されません (、`<?xml…>`宣言は PI 情報項目と見なされません)

- [notations] セットは空です。

- [unparsed entities] セットは空です。

例:JSON へのマッピングのため、次のドキュメントを持たない [children] PI とコメントを保持します。

```xml
<?xml version="1.0"?>
<!--comment--><?pi?>
<root type="number">42</root>
```

Root JSON Element としての EII には次の特性があります。

- [local name] は値 "root" を持ちます。

- [namespace name] は値を持ちません。

- [prefix] は値を持ちません。

- [children] には、後述するように内部要素である EII、または文字情報項目 (CII: Character Information Item) のいずれか一方が含まれる場合と、どちらも含まれない場合がありますが、両方とも含まれることはありません。

- [attributes] には、次のオプションの属性情報項目 (AII: Attribute Information Item) が含まれる場合があります。

- 後述の JSON Type Attribute ("type")。 この属性は、マップされた XML で JSON 型 (文字列、数値、ブール値、オブジェクト、配列、または null) を保持するのに使用します。

- Data Contract Name Attribute ("\_\_型")、後述するようです。 この属性は、JSON Type Attribute が存在し、その [normalized value] が "object" であるときにのみ存在します。 この属性は、派生型がシリアル化されたり、基本型が要求されたりするポリモーフィックな場合などに、`DataContractJsonSerializer` によりデータ コントラクトの型情報を保持するために使用されます。 `DataContractJsonSerializer` を使用していなければ、この属性はほとんどの場合に無視されます。

- [スコープ内の名前空間] に"xml"のバインドを含む`http://www.w3.org/XML/1998/namespace`infoset 仕様で要件に従う。

- [children]、[attributes]、および[in-scope namespaces] は、あらかじめ指定した項目以外の項目を持つことができず、[namespace attributes] はメンバーを持つことができませんが、JSON からマップされた XML を読み取るときには、この事実に依存しないでください。

例:JSON へのマッピングのため、次のドキュメントを持たない [名前空間の属性] が空でないです。

```xml
<?xml version="1.0"?>
<root xmlns:a="myattributevalue">42</root>
```

JSON Type Attribute としての AII には次の特性があります。

- [namespace name] は値を持ちません。
- [prefix] は値を持ちません。
- [local name] は "type" です。
- [normalized value] は、次のセクションで説明する型の値のいずれかになります。
- [specified] は `true` です。
- [attribute type] は値を持ちません。
- [references] は値を持ちません。

Data Contract Name Attribute としての AII には次の特性があります。

- [namespace name] は値を持ちません。
- [prefix] は値を持ちません。
- [local name] は"\_\_型"(2 つのアンダー スコアと"type")。
- [normalized value] は、任意の有効な Unicode 文字列です。この文字列から JSON へのマッピングは、次のセクションで説明します。
- [specified] は `true` です。
- [attribute type] は値を持ちません。
- [references] は値を持ちません。

Root JSON Element に含まれる内部要素、またはその他の内部要素には、次の特性があります。

- [ローカル名] には、さらに説明されている任意の値が場合があります。
- [namespace name]、[prefix]、[children]、[attributes]、[namespace attributes]、および [in-scope namespaces] は、Root JSON Element と同じ規則に従います。

Root JSON Element および内部要素では、JSON Type Attribute により JSON へのマッピングと、[children] およびその解釈が定義されます。 属性の [normalized value] は大文字小文字を区別、小文字にする必要があり、空白文字を含めることはできません。

|[normalized 値] の JSON Type Attribute としての AII|対応する EII の許可された [children]|JSON へのマッピング|
|---------------------------------------------------------|---------------------------------------------------|---------------------|
|`string` (または JSON 型 AII なし)<br /><br /> `string` および JSON 型 AII なしは同じです。`string` を既定値にします。<br /><br /> その結果、`<root> string1</root>` が JSON `string` "string1" にマップされます。|0 または複数の Cii|JSON `string` (JSON RFC section 2.5)。 `char` はそれぞれ、CII の [character code] に対応する文字です。 CII が存在しない場合は、空の JSON `string` にマップされます。<br /><br /> 例:次の要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="string">42</root>`<br /><br /> JSON フラグメントは "42" です。<br /><br /> XML から JSON へのマッピングでは、エスケープする必要がある文字はエスケープ文字にマップされ、その他はすべて、エスケープされない文字にマップされます。 「/」文字が特別な – はエスケープすることはありませんが (として書き出さ"\\/")。<br /><br /> 例:次の要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="string">the "da/ta"</root>`<br /><br /> JSON フラグメントは"、 \\"da\\/ta\\""です。<br /><br /> JSON から XML へのマッピングでは、エスケープ文字およびエスケープされない文字が、対応する [character code] に正しくマップされます。<br /><br /> 例:JSON フラグメント"\u0041BC"は、次の XML 要素にマップされます。<br /><br /> `<root type="string">ABC</root>`<br /><br /> 文字列は、XML にマップされない空白文字 (JSON rfc section 2 の ' ws') で囲むことができます。<br /><br /> 例:JSON フラグメント"ABC"、(最初の二重引用符の前にスペースがありますが)、次の XML 要素にマップされます。<br /><br /> `<root type="string">ABC</root>`<br /><br /> XML 内の任意の空白は、JSON の空白部分にマップされます。<br /><br /> 例:次の XML 要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="string">  A BC      </root>`<br /><br /> JSON フラグメントは " A BC " です。|
|`number`|1 個以上の CII|JSON `number` (JSON RFC section 2.4) が空白で囲まれた可能性があります。 数/空白文字の組み合わせ内の各文字は、cii の [character code] に対応する文字です。<br /><br /> 例:次の要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="number">    42</root>`<br /><br /> JSON フラグメントは    42 です <br /><br /> (空白が保持されます)。|
|`boolean`|4 または 5 の Cii (に対応する`true`または`false`)、追加の空白の Cii で囲まれている可能性があります。|文字列 "true" に対応する CII シーケンスは、リテラルの `true` にマップされ、文字列 "false" に対応する CII シーケンスは、リテラルの `false` にマップされます。 周囲の空白は保持されます。<br /><br /> 例:次の要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="boolean"> false</root>`<br /><br /> JSON フラグメントは `false` です。|
|`null`|いずれも許可されません。|リテラルの `null`。 Json XML へのマッピングから、 `null` XML にマップされない空白文字 (section 2 の ' ws') で囲むことがあります。<br /><br /> 例:次の要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="null"/>`<br /><br /> または<br /><br /> `<root type="null"></root>`<br /><br /> :<br /><br /> いずれの場合も、JSON フラグメントは `Null` です。|
|`object`|0 個以上の EII|JSON RFC section 2.2 にあるように、`begin-object` (左中かっこ) の直後に、後述するように各 EII のメンバー レコードが続きます。 EII が複数個存在する場合、メンバー レコードの間に値区切り記号 (コンマ) が配置されます。 最後尾には、end-object (右中かっこ) が置かれます。<br /><br /> 例:次の要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="object">`<br /><br /> `<type1 type="string">aaa\</type1>`<br /><br /> `<type2 type="string">bbb\</type2>`<br /><br /> `</root >`<br /><br /> JSON フラグメントは `{"type1":"aaa","type2":"bbb"}` です。<br /><br /> XML から JSON へのマッピングに Data Contract Type Attribute が存在する場合は、最初に追加のメンバー レコードが挿入されます。 その名前がデータ コントラクト型の属性の [local name] ("\_\_型")、その値はの [normalized value] 属性とします。 逆に、JSON と XML のマッピングを最初のメンバー レコードの名前がデータ コントラクト型の属性の [local name] の場合に (つまり、"\_\_型")、対応する Data Contract Type Attribute がマップされた XML に存在するが、対応する EII は存在しません。 また、このような特定のマッピングが適用されるには、このメンバー レコードが最初に JSON オブジェクトに存在している必要があります。 これは、メンバー レコードの順序が重要ではない通常の JSON 処理とは異なっています。<br /><br /> 例:<br /><br /> 次の JSON フラグメントは XML にマップされます。<br /><br /> `{"__type":"Person","name":"John"}`<br /><br /> XML は次のコードです。<br /><br /> `<root type="object" __type="Person">   <name type="string">John</name> </root>`<br /><br /> いることを確認、 \_\_型 aii なしはあるが、あるありません\_ \_EII を入力します。<br /><br /> ただし、次の例に示すように、JSON での順序が逆になる場合があります。<br /><br /> {"name":"John","\_\_type":"Person"}<br /><br /> このとき、対応する XML は次のとおりです。<br /><br /> `<root type="object">   <name type="string">John</name>   <__type type="string">Person</__type> </root>`<br /><br /> つまり、 \_AII ではない、EII に対応して特別な意味を通常どおりが種類 (_t) 停止します。<br /><br /> JSON 値にマップされるときの、AII の [normalized value] に対するエスケープ/エスケープ解除ルールは、このテーブルの "string" 行で指定された JSON 文字列に対するルールと同じです。<br /><br /> 例:<br /><br /> `<root type="object" __type="\abc" />`<br /><br /> これを前の例に適用すると、次の JSON にマップされます。<br /><br /> `{"__type":"\\abc"}`<br /><br /> Xml JSON へのマッピングから、最初の EII の [ローカル名] することはできません"\_\_型"です。<br /><br /> 空白文字 (`ws`) オブジェクトの JSON へのマッピングを XML に生成されませんし、json と XML のマッピングは無視されます。<br /><br /> 例:次の JSON フラグメントは XML 要素にマップされます。<br /><br /> `{ "ccc" : "aaa", "ddd" :"bbb"}`<br /><br /> XML 要素を、次のコードで示します。<br /><br /> `<root type="object">    <ccc type="string">aaa</ccc>    <ddd type="string">bbb</bar> </root >`|
|array|0 個以上の EII|JSON RFC section 2.3 にあるように、begin-array (左角かっこ) の直後に、後述する各 EII の配列レコードが続きます。 EII が複数個存在する場合、配列レコードの間に値区切り記号 (コンマ) が配置されます。 最後尾には、end-array が置かれます。<br /><br /> 例:次の XML 要素は、JSON フラグメントにマップされます。<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`<br /><br /> JSON フラグメントは ["aaa","bbb"] です。<br /><br /> 空白文字 (`ws`) 配列の JSON へのマッピングを XML に生成されませんし、json と XML のマッピングは無視されます。<br /><br /> 例:JSON フラグメントです。<br /><br />`["aaa", "bbb"]`<br /><br /> マップされる XML 要素は、次のとおりです。<br /><br /> `<root type="array"/>    <item type="string">aaa</item>    <item type="string">bbb</item> </root >`|

メンバー レコードの動作は次のとおりです。

- JSON RFC section 2.2 で規定されるように、内部要素の [local name] は `string` の `member` 部分にマップされます。

例:次の要素は、JSON フラグメントにマップされます。

`<root type="object"/>`

`<myLocalName type="string">aaa</myLocalName>`

`</root >`

次の JSON フラグメントが示されます。

`{"myLocalName":"aaa"}`

- XML から JSON へのマッピングでは、JSON でエスケープする必要がある文字はエスケープされ、それ以外はエスケープされません。 "/" 文字は、エスケープする必要のない文字ですが、エスケープされます (JSON から XML へのマッピングではエスケープする必要はありません)。 これは、JSON の `DateTime` データに対する ASP.NET AJAX 形式をサポートするために必要な処理です。

- JSON から XML へのマッピングでは、すべての文字が (必要に応じて非エスケープ文字も含む) [local name] を生成する `string` を形成するために使用されます。

- 内部要素 [children] は `JSON Type Attribute` の場合と同じように、`Root JSON Element` に従って section 2.2 の値にマップされます。 EII の複数レベルの入れ子 (配列内の入れ子も含む) が許可されます。

例:次の要素は、JSON フラグメントにマップされます。

```xml
<root type="object">
    <myLocalName1 type="string">myValue1</myLocalName1>
    <myLocalName2 type="number">2</myLocalName2>
    <myLocalName3 type="object">
        <myNestedName1 type="boolean">true</myNestedName1>
        <myNestedName2 type="null"/>
    </myLocalName3>
</root >
```

マップされる JSON フラグメントは次のとおりです。

`{"myLocalName1":"myValue1","myLocalName2":2,"myLocalName3":{"myNestedName1":true,"myNestedName2":null}}`

> [!NOTE]
> 上記のマッピングには、XML エンコーディングの手順がありません。 そのため、WCF は、キー名のすべての文字が XML 要素名に有効な文字を JSON ドキュメントのみをサポートします。 たとえば、JSON ドキュメント {"<":"a"} はサポートされていません < XML 要素の有効な名前がありません。

逆に、XML では有効であり、JSON では有効でない文字は、上記のマッピングに JSON のエスケープ/エスケープ解除の手順が含まれるため、問題が生じません。

Array Record の動作は次のとおりです。

- 内部要素の [local name] は "item" です。

- 内部要素の [children] は、Root JSON Element の場合と同じように、JSON Type Attribute に従って section 2.3 の値にマップされます。 EII の複数の入れ子 (オブジェクト内の入れ子も含む) が許可されます。

例:次の要素は、JSON フラグメントにマップされます。

```xml
<root type="array"/>
    <item type="string">myValue1</item>
    <item type="number">2</item>
    <item type="array">
    <item type="boolean">true</item>
    <item type="null"/></item>
</root >
```

JSON フラグメントは次のとおりです。

`["myValue1",2,[true,null]]`

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization.Json.JsonReaderWriterFactory>
- <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>
- [スタンドアロン JSON のシリアル化](stand-alone-json-serialization.md)
