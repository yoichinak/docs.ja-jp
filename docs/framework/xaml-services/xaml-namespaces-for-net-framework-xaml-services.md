---
title: .NET Framework XAML サービス用の XAML 名前空間
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: dc2c424306b9ebd705f2541266e4b1e3afe94547
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153557"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>.NET Framework XAML サービス用の XAML 名前空間
XAML 名前空間は、XML 名前空間の定義を拡張する概念です。 XML 名前空間と同様に、定義できますを使用して XAML 名前空間、`xmlns`マークアップ内の属性。 XAML 名前空間は、XAML ノード ストリームでその他の XAML サービス Api も表記されます。 このトピックでは、XAML 名前空間の概念を定義し、XAML 名前空間を定義することができますおよび XAML スキーマ コンテキストやその他のさまざまな .NET Framework XAML サービスで使用する方法について説明します。  
  
## <a name="xml-namespace-and-xaml-namespace"></a>XML の Namespace および XAML Namespace  
 XAML 名前空間は、XAML は XML の特殊な形式で、マークアップの基本的な XML 形式を使用すると同様に特殊化された XML 名前空間が。 マークアップでは、XAML 名前空間とそのマッピングを宣言する、`xmlns`要素に適用される属性。 `xmlns`で XAML 名前空間が宣言されている同じ要素に対する宣言できます。 要素に対する XAML 名前空間の宣言では、その要素をその要素のすべての属性とその要素の子をすべて有効です。 属性がない、属性を格納する要素と同じで、属性名自体は、マークアップでは、その属性名の一部として、プレフィックスを参照する XAML 名前空間を使用できます。  
  
 XML 名前空間と XAML 名前空間の違いは、XML 名前空間は、スキーマを参照するために使用可能性がありますか、単にエンティティを区別するためにされる可能性がありますです。 、XAML とバッキング型、に型とメンバーの XAML で使用するためを解決する必要があります最終的に、XML スキーマの概念は、この機能には適用されません。 XAML 名前空間には、XAML スキーマ コンテキストをこの型のマッピングを実行するために使用できる必要がある情報が含まれています。  
  
## <a name="xaml-namespace-components"></a>XAML Namespace コンポーネント  
 XAML 名前空間の定義が 2 つのコンポーネント。 プレフィックス、および識別子。 これらの各コンポーネントは、XAML 名前空間が、マークアップで宣言または XAML 型システムで定義されている場合に存在します。  
  
 許可されるよう、プレフィックスは任意の文字列を使用できる、 [XML 1.0 仕様での W3C 名前空間](https://go.microsoft.com/fwlink/?LinkID=161735)します。 慣例により、プレフィックスは、プレフィックスが、一般的なマークアップ ファイルで何度も繰り返すために、通常は非常に短い文字列をします。 複数の XAML 実装で使用することを意図した特定の XAML 名前空間は、特定の従来のプレフィックスを使用します。 たとえば、XAML 言語の XAML 名前空間は通常、マップ、プレフィックスを使用して`x`します。 既定 XAML 名前空間プレフィックスが定義には付与しませんが、定義または脅かさ Framework XAML サービス API のクエリを実行する場合は、空の文字列として表されるを定義することができます。 通常、既定の XAML 名前空間は、プレフィックス省略量の最大化を促進するために選択されます意図的に XAML 実装テクノロジ、シナリオ、およびボキャブラリをマークアップします。  
  
 許可されているように、識別子が任意の文字列を使用できます、 [XML 1.0 仕様での W3C 名前空間](https://go.microsoft.com/fwlink/?LinkID=161735)します。 慣例により、XML 名前空間または XAML 名前空間のいずれかの識別子は多くの場合、指定された URI の形式でプロトコルで修飾された絶対 URI として通常。 多くの場合、特定の XAML ボキャブラリを定義するバージョン情報がパス文字列の一部として暗黙的に指定します。 XAML 名前空間は、XML URI 規則を超える、追加の識別子の規則を追加します。 XAML 名前空間識別子は、その XAML 名前空間の下の要素として指定されている型を解決するために、またはメンバーに属性を解決するのには、XAML スキーマ コンテキストで必要な情報を通信します。  
  
 XAML スキーマ コンテキスト情報を伝達するために、XAML 名前空間の識別子が引き続き URI 形式でできます。 ただし、この場合、URI もとして宣言されます、特定のアセンブリまたはアセンブリの一覧に一致する識別子。 これは、アセンブリ内で属性を持つアセンブリ<xref:System.Windows.Markup.XmlnsDefinitionAttribute>します。 XAML 名前空間を識別して、属性付きアセンブリの CLR ベースの型の解決の動作をサポートしているは、このメソッドは .NET Framework XAML サービスでの既定の XAML スキーマ コンテキストでサポートされています。 一般的には、この規則は、場合、XAML スキーマ コンテキストが、CLR が組み込まれていますか、CLR アセンブリの CLR 属性を読み取るために必要な既定 XAML スキーマ コンテキストに基づきます使用できます。  
  
 XAML 名前空間は、CLR 名前空間と型を定義するアセンブリと通信する規則によっても識別できます。 ない場合にこの規則が使用<xref:System.Windows.Markup.XmlnsDefinitionAttribute>型が含まれるアセンブリに属性が存在します。 この規則は、可能性のある、URI 規則よりも複雑ですし、アセンブリを参照する複数の方法があるため、あいまいさと、重複が発生する可能性があります。  
  
 CLR 名前空間とアセンブリの規則を使用する識別子の最も基本的な形式は次のとおりです。  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` `; assembly=`は、構文のリテラルのコンポーネントです。  
  
 *clrnsName*は CLR 名前空間を識別する名前文字列です。 この文字列名には、CLR 名前空間とその他の CLR 名前空間との関係についてのヒントを提供する内部ドット文字 (.) が含まれています。  
  
 *assemblyShortName*は XAML 内で使用される型を定義するアセンブリの名前文字列です。 アセンブリによって定義され、によって指定された CLR 名前空間内で宣言する具体的には、宣言された XAML 名前空間を介してアクセスされる型が予想される*clrnsName*します。 通常、この文字列名にはによって報告された情報は対応して<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>します。  
  
 CLR 名前空間とアセンブリの規則のより完全な定義は次のとおりです。  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName*として有効な任意の文字列を表す、<xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>入力します。 この文字列は、カルチャ、公開キー、またはバージョン情報を含めることができます (これらの概念の定義がのリファレンス トピックで定義されている<xref:System.Reflection.Assembly>)。 COFF 形式および証拠 (の他のオーバー ロードで使用される<xref:System.Reflection.Assembly.Load%2A>) 上の目的を読み込む XAML アセンブリの関係のないすべての負荷情報を文字列として表示する必要があります。  
  
 XAML セキュリティ、またはアセンブリの簡易名、によって読み込まれるまたはキャッシュまたはアプリケーション ドメインに事前に存在する場合に存在できるであいまいさを削除するための便利な方法は、アセンブリの公開キーを指定します。 詳細については、次を参照してください。 [XAML セキュリティの考慮事項](xaml-security-considerations.md)します。  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>XAML サービス API で XAML Namespace 宣言  
 XAML サービス API では、XAML 名前空間宣言によって表される、<xref:System.Xaml.NamespaceDeclaration>オブジェクト。 呼び出すコードでの XAML 名前空間を宣言している場合、<xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>コンス トラクター。 `ns`と`prefix`パラメーターは、文字列として指定して、これらのパラメーターを提供する入力 XAML 名前空間の識別子と XAML 名前空間プレフィックスの定義に対応するようにこのトピックで既に提供されています。  
  
 または、XAML 型システムへの他のアクセスにより、XAML ノード ストリームの一部としての XAML 名前空間の情報が見つかった場合<xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType>XAML 名前空間の識別子を報告および<xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType>XAML 名前空間プレフィックスを報告します。  
  
 XAML ノード ストリームで XAML 名前空間の情報は、それを適用するエンティティの前にある XAML ノードとして表示できます。 XAML 名前空間の情報がよりも前の場合など、`StartObject`の XAML ルート要素。 詳細については、「 [Understanding XAML Node Stream Structures and Concepts](understanding-xaml-node-stream-structures-and-concepts.md)」を参照してください。  
  
 .NET Framework XAML サービス API を使用する多くのシナリオでは、存在しますが、少なくとも 1 つの XAML 名前空間宣言が必要ですし、宣言は必要がありますが含まれているか、XAML スキーマ コンテキストで必要な情報を参照してください。 XAML 名前空間は、アセンブリを読み込む、または名前空間と既に読み込まれてまたは XAML スキーマ コンテキストで認識されているアセンブリ内の特定の型の解決に役立つを指定する必要がありますか。  
  
 XAML ノード ストリームを生成するために XAML の種類の情報は、XAML スキーマ コンテキストで使用できるにある必要があります。 最初に作成するには、各ノードに関連する XAML 名前空間を決定することがなく、XAML の型情報を特定できません。 この時点では、型のインスタンスをまだ作成されていないが、XAML スキーマ コンテキストを定義するアセンブリと型をバックアップからの情報を検索する必要があります。 たとえば、マークアップを処理するために`<Party><PartyFavor/></Party>`、XAML スキーマ コンテキストの種類と名前を決定できる必要があります、`ContentProperty`の`Party`、したがっても知る必要がありますの XAML 名前空間の情報と`Party`と`PartyFavor`します。 既定の XAML スキーマ コンテキストの場合は、静的リフレクションは、多くのノード ストリームで XAML の種類のノードを生成するために必要な XAML 型システム情報を報告します。  
  
 XAML ノード ストリームからオブジェクト グラフを生成するために、元のマークアップで使用され、XAML ノード ストリームに記録する各 XAML プレフィックスの XAML 名前空間宣言があります。 この時点では、インスタンスが作成されると true 型マッピングの動作が発生します。  
  
 内の XML 名前空間宣言を宣言する 1 つの手法を使用することができますが、XAML 名前空間を使用する XAML スキーマ コンテキストをするマークアップでは、未定義の場合、XAML 名前空間の情報を事前に設定する必要がある場合、 <xref:System.Xml.XmlParserContext> の<xref:System.Xml.XmlReader>. 使用して<xref:System.Xml.XmlReader>XAML リーダーのコンス トラクターに対する入力としてまたは<xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>します。  
  
 XAML 名前空間の .NET Framework XAML サービスで処理に関連するその他の 2 つの API は、属性<xref:System.Windows.Markup.XmlnsDefinitionAttribute>と<xref:System.Windows.Markup.XmlnsPrefixAttribute>します。 これらの属性は、アセンブリに適用されます。 <xref:System.Windows.Markup.XmlnsDefinitionAttribute> URI を含むすべて XAML 名前空間宣言を解釈する XAML スキーマ コンテキストによって使用されます。 <xref:System.Windows.Markup.XmlnsPrefixAttribute> 特定の XAML 名前空間は、予測可能なプレフィックスでシリアル化できるように、XAML を生成するツールによって使用されます。 詳細については、次を参照してください。[カスタム型およびライブラリの CLR 属性を XAML-Related](xaml-related-clr-attributes-for-custom-types-and-libraries.md)します。  
  
## <a name="see-also"></a>関連項目

- [XAML ノード ストリームの構造と概念について](understanding-xaml-node-stream-structures-and-concepts.md)
