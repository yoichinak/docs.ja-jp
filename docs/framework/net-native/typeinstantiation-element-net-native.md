---
title: <TypeInstantiation> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4244d47c099fe7a5b0093b94ef44b4354bae86f1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173135"
---
# <a name="typeinstantiation-element-net-native"></a>\<TypeInstantiation > 要素 (.NET ネイティブ)
構築されたジェネリック型にランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
                   Activate="policy_type"  
                   Browse="policy_type"  
                   Dynamic="policy_type"  
                   Serialize="policy_type"  
                   DataContractSerializer="policy_setting"  
                   DataContractJsonSerializer="policy_setting"  
                   XmlSerializer="policy_setting"  
                   MarshalObject="policy_setting"  
                   MarshalDelegate="policy_setting"  
                   MarshalStructure="policy_setting" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 型名を指定します。|  
|`Arguments`|全般|必須の属性です。 ジェネリック型引数を指定します。 複数の引数が存在する場合は、コンマで区切られます。|  
|`Activate`|リフレクション|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|リフレクション|省略可能な属性です。 プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。|  
|`Dynamic`|リフレクション|省略可能な属性です。 コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。|  
|`Serialize`|シリアル化|省略可能な属性です。 コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。|  
|`DataContractSerializer`|シリアル化|省略可能な属性です。 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。|  
|`DataContractJsonSerializer`|シリアル化|省略可能な属性です。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。|  
|`XmlSerializer`|シリアル化|省略可能な属性です。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。|  
|`MarshalObject`|Interop|省略可能な属性です。 Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。|  
|`MarshalDelegate`|Interop|省略可能な属性です。 ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。|  
|`MarshalStructure`|Interop|省略可能な属性です。 ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*type_name*|型名。 この `<TypeInstantiation>` 要素が [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) 要素、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素、または別の `<TypeInstantiation>` 要素の子である場合、*type_name* には名前空間なしで型の名前を指定できます。 それ以外の場合は、*type_name* には完全修飾型名を含める必要があります。 型名は修飾されません。 たとえば、<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> オブジェクトの場合、`<TypeInstantiation>` 要素は次のように示されることがあります。<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>引数属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*type_argument*|ジェネリック型引数を指定します。 複数の引数が存在する場合は、コンマで区切られます。 各引数は、完全修飾型名で構成されている必要があります。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*policy_setting*|構築されたジェネリック型のこのポリシーの種類に適用する設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|この型に属するイベントにリフレクション ポリシーを適用します。|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|この型に属するフィールドにリフレクション ポリシーを適用します。|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|型にポリシーを適用します (それを含む `<TypeInstantiation>` 要素により表される型にそのポリシーが適用されている場合)。|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|この型に属するメソッドにリフレクション ポリシーを適用します。|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|この型に属するプロパティにリフレクション ポリシーを適用します。|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|入れ子になった型にリフレクション ポリシーを適用します。|  
|`<TypeInstantiation>`|入れ子になった構築されたジェネリック型にリフレクション ポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|名前空間内のすべての型にリフレクション ポリシーを適用します。|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|`<TypeInstantiation>`|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>Remarks  
 リフレクション、シリアル化、および相互運用属性はすべて省略可能です。 ただし、そのうち少なくとも 1 つが存在する必要があります。  
  
 `<TypeInstantiation>` 要素が [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)、[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)、[\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素の子である場合、親要素により定義されたポリシー設定をオーバーライドします。 [\<Type>](../../../docs/framework/net-native/type-element-net-native.md) 要素が対応するジェネリック型定義を定義している場合、`<TypeInstantiation>` 要素は、指定の構築されたジェネリック型のインスタンス化についてのみランタイム リフレクション ポリシーをオーバーライドします。  
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、構築された <xref:System.Collections.Generic.Dictionary%602> オブジェクトからジェネリック型定義を取得します。 また、リフレクションを使用して、構築されたジェネリック型とジェネリック型定義を表す <xref:System.Type> オブジェクトに関する情報も表示します。 変数`b`の例では、<xref:Windows.UI.Xaml.Controls.TextBlock>コントロール。  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンでコンパイルされると、この例は <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=nameWithType> メソッドを呼び出す行で [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) 例外をスローします。 次の `<TypeInstantiation>` 要素をランタイム ディレクティブ ファイルに追加すると、この例外を排除して、必要なメタデータを提供できます。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)
- [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
