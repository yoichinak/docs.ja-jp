---
title: <Type> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a92e6627ba937b10b183a833a005792f0a51f921
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162699"
---
# <a name="type-element-net-native"></a>\<型 > 要素 (.NET ネイティブ)
クラスや構造体などの特定の型に実行時ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Type Name="type_name"  
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
|`Activate`|リフレクション|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|リフレクション|省略可能な属性です。 プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。|  
|`Dynamic`|リフレクション|省略可能な属性です。 コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。|  
|`Serialize`|シリアル化|省略可能な属性です。 コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。|  
|`DataContractSerializer`|シリアル化|省略可能な属性です。 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> クラスを使用するシリアル化のポリシーを制御します。|  
|`DataContractJsonSerializer`|シリアル化|省略可能な属性です。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType> クラスを使用する JSON シリアル化のポリシーを制御します。|  
|`XmlSerializer`|シリアル化|省略可能な属性です。 <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> クラスを使用する XML シリアル化のポリシーを制御します。|  
|`MarshalObject`|Interop|省略可能な属性です。 Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。|  
|`MarshalDelegate`|Interop|省略可能な属性です。 ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。|  
|`MarshalStructure`|Interop|省略可能な属性です。 値型をネイティブ コードにマーシャリングするためのポリシーを制御します。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*type_name*|型名。 この `<Type>` 要素が [\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md) 要素または別の `<Type>` 要素のいずれかの子である場合、*type_name* には名前空間なしで型の名前を含めることができます。 それ以外の場合は、*type_name* には完全修飾型名を含める必要があります。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*policy_setting*|このポリシーの種類に適用する設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<AttributeImplies>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|含んでいる型が属性の場合は、その属性が適用されるコード要素の実行時ポリシーを定義します。|  
|[\<Event>](../../../docs/framework/net-native/event-element-net-native.md)|この型に属するイベントにリフレクション ポリシーを適用します。|  
|[\<Field>](../../../docs/framework/net-native/field-element-net-native.md)|この型に属するフィールドにリフレクション ポリシーを適用します。|  
|[\<GenericParameter>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|ジェネリック型のパラメーターの型にポリシーを適用します。|  
|[\<ImpliesType>](../../../docs/framework/net-native/impliestype-element-net-native.md)|型にポリシーを適用します (それを含む `<Type>` 要素により表される型にそのポリシーが適用されている場合)。|  
|[\<Method>](../../../docs/framework/net-native/method-element-net-native.md)|この型に属するメソッドにリフレクション ポリシーを適用します。|  
|[\<MethodInstantiation>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。|  
|[\<Property>](../../../docs/framework/net-native/property-element-net-native.md)|この型に属するプロパティにリフレクション ポリシーを適用します。|  
|[\<Subtypes>](../../../docs/framework/net-native/subtypes-element-net-native.md)|それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。|  
|`<Type>`|入れ子になった型にリフレクション ポリシーを適用します。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型にリフレクション ポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)|指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|名前空間内のすべての型にリフレクション ポリシーを適用します。|  
|`<Type>`|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>Remarks  
 リフレクション、シリアル化、および相互運用属性はすべて省略可能です。 いずれも存在しない場合、`<Type>` 要素は、その子型が個々のメンバーのポリシーを定義するコンテナーとして機能します。  
  
 `<Type>` 要素が [\<Assembly>](../../../docs/framework/net-native/assembly-element-net-native.md)、[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)、`<Type>`、[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素の子である場合、親要素によって定義されたポリシー設定をオーバーライドします。  
  
 ジェネリック型の `<Type>` 要素は、独自のポリシーを持たないすべてのインスタンス化にそのポリシーを適用します。 構築されたジェネリック型のポリシーは、[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) 要素により定義されます。  
  
 型がジェネリック型の場合、アクサン グラーブ記号 (\`) の後ろにジェネリック パラメーターの数を付けたもので名前が修飾されます。 たとえば、`Name` クラスの `<Type>` 要素の <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 属性は、``Name="System.Collections.Generic.List`1"`` と示されます。
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、<xref:System.Collections.Generic.List%601?displayProperty=nameWithType> クラスのフィールド、プロパティ、およびメソッドに関する情報を表示します。 変数`b`の例では、<xref:Windows.UI.Xaml.Controls.TextBlock>コントロール。 この例は単に型情報を取得するのみであるため、メタデータの可用性は `Browse` ポリシー設定により制御されます。  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 <xref:System.Collections.Generic.List%601> クラスのメタデータは [!INCLUDE[net_native](../../../includes/net-native-md.md)] ツール チェーンにより自動的に含められないため、例では実行時に要求されたメンバー情報を表示できません。 必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。 親要素 [<Namespace\>](../../../docs/framework/net-native/namespace-element-net-native.md) を指定しているため、`<Type>` 要素で完全修飾型名を指定する必要はないことに注意してください。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
```  
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、<xref:System.Reflection.PropertyInfo> プロパティを表す <xref:System.String.Chars%2A?displayProperty=nameWithType> オブジェクトを取得します。 続けて、<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> メソッドを使用して文字列の 7 番目の文字の値を取得し、文字列のすべての文字を表示します。 変数`b`の例では、<xref:Windows.UI.Xaml.Controls.TextBlock>コントロール。  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 <xref:System.String> オブジェクトのメタデータは使用できないため、<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=nameWithType> ツール チェーンでコンパイルした場合、実行時に <xref:System.NullReferenceException> メソッドを呼び出すと [!INCLUDE[net_native](../../../includes/net-native-md.md)] 例外がスローされます。 例外を排除し、必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
```  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)
- [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
