---
title: <Assembly> 要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: cfe629eb-1106-4113-86e1-052f402d8d8b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c0788c05edace2142d348c679c73aa1b4404ce75
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137853"
---
# <a name="assembly-element-net-native"></a>\<アセンブリ > 要素 (.NET ネイティブ)
指定したアセンブリ内のすべての型にランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Assembly Name="assembly_name"   
          Activate="policy_setting"  
          Browse="policy_setting"  
          Dynamic="policy_setting"  
          Serialize="policy_setting"  
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
|`Name`|全般|必須の属性です。 アセンブリの簡易名を指定します。|  
|`Activate`|リフレクション|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|リフレクション|省略可能な属性です。 アセンブリ内の型に関する情報の照会または型の列挙を制御しますが、実行時の動的アクセスは有効にしません。|  
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
|*assembly_name*|ファイル拡張子のないアセンブリの簡易名です。 この属性は、<xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> プロパティに対応します。 たとえば、Extensions.dll というアセンブリの名前は "Extensions" です。<br /><br /> リテラル文字列 `*Application*` を指定して、アプリ パッケージ内のすべてのアセンブリに、読み込みの有無に関係なくポリシーを適用することもできます。 `*Application*` は、.NET Framework アセンブリにポリシーを適用しません。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|[値]|説明|  
|-----------|-----------------|  
|*policy_setting*|アセンブリ内のすべての型について、このポリシーの種類に適用する設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、「[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Namespace>](../../../docs/framework/net-native/namespace-element-net-native.md)|子名前空間内のすべての型にリフレクション ポリシーを適用します。|  
|[\<Type>](../../../docs/framework/net-native/type-element-net-native.md)|型にリフレクション ポリシーを適用します。|  
|[\<TypeInstantiation>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型にリフレクション ポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。 [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素には、0 個以上の `<Assembly>` 要素を含めることができます。|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。 [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素には、0 または 1 個の `<Assembly>` 要素を含めることができます。|  
  
## <a name="remarks"></a>Remarks  
 `<Assembly>` 要素は、アセンブリ内のすべての型の実行時ポリシーを定義します。 これは、ライブラリを指定するが、ランタイム リフレクション ポリシーの定義は子要素に依存する [\<Library>](../../../docs/framework/net-native/library-element-net-native.md) 要素とは異なります。 `<Assembly>` 要素は、子要素でオーバーライドされない限り、アセンブリ内のすべての型に適用されます。  
  
 次の例では、`Name` 属性に "*Application\*" という値を割り当てて、アプリ パッケージ内のアセンブリのすべての型に実行時ポリシーを適用する方法を示しています。 `<Assembly>` 要素は [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) 要素の子である必要があります。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">   
  <Application>   
     <Assembly Name="*Application*" Dynamic="Required All" />   
  </Application>   
</Directives>  
```  
  
 `Activate` 属性、`Browse` 属性、`Dynamic`、および `Serialize` 属性はすべて省略可能です。 ただし、`<Assembly>` 要素にはこれらの属性のいずれか 1 つ以上を含める必要があります。  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)
- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)
