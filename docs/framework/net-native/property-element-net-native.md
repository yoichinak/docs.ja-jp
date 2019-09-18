---
title: <Property>要素 (.NET ネイティブ)
ms.date: 03/30/2017
ms.assetid: ad4ba56d-3bcb-4c10-ba90-1cc66e2175a1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54daf15c593327bf3255f40f6eb6931ffc8bd3c6
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049312"
---
# <a name="property-element-net-native"></a>\<プロパティ > 要素 (.NET ネイティブ)
プロパティにランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
<Property Name="property_name"  
          Browse="policy_type"  
          Dynamic="policy_type"  
          Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 プロパティ名を指定します。|  
|`Browse`|リフレクション|省略可能な属性です。 プロパティに関する情報の照会やプロパティの列挙を制御しますが、実行時の動的アクセスは有効にしません。|  
|`Dynamic`|リフレクション|省略可能な属性です。 プロパティへの実行時アクセスを制御して、動的プログラミングを有効にします。 このポリシーによって、実行時にプロパティを動的に設定または取得できるようになります。|  
|`Serialize`|シリアル化|省略可能な属性です。 プロパティへの実行時アクセスを制御して、型インスタンスを Newtonsoft の JSON シリアライザーなどのライブラリによってシリアル化できるようにしたり、データ バインディングで使用できるようにしたりします。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|値|説明|  
|-----------|-----------------|  
|*method_name*|プロパティ名。 プロパティの型は、親の [\<Type>](type-element-net-native.md) または [\<TypeInstantiation>](typeinstantiation-element-net-native.md) 要素により定義されます。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|値|説明|  
|-----------|-----------------|  
|*policy_setting*|プロパティのこのポリシーの種類に適用する設定です。 指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。 詳細については、「[ランタイム ディレクティブのポリシー設定](runtime-directive-policy-settings.md)」を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>Remarks  
 プロパティのポリシーが明示的に定義されていない場合は、親要素の実行時ポリシーを継承します。  
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、`Book` オブジェクトをインスタンス化し、そのプロパティ値を表示します。 プロジェクトの既定の default.rd.xml ファイルは、次のように示されます。  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Namespace Name="LibraryApplications"  Browse="Required Public" >  
         <Type Name="Book"   Activate="All" />  
      </Namespace>  
   </Application>  
</Directives>  
```  
  
 このファイルは、`All` クラスの `Activate` ポリシーに `Book` 値を適用します。これにより、リフレクションを介してクラス コンストラクターにアクセスできるようになります。 `Browse` クラスの `Book` ポリシーは、その親名前空間から継承されます。 これは `Required Public` に設定され、メタデータが実行時に使用できるようになります。  
  
 この例のソース コードを次に示します。 変数`outputBlock`は、コントロール<xref:Windows.UI.Xaml.Controls.TextBlock>を表します。  
  
 [!code-csharp[ProjectN_Reflection#6](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/property1.cs#6)]  
  
 ただし、この例をコンパイルして実行すると、[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) 例外がスローされます。 `Book` 型のメタデータは使用可能になりましたが、プロパティの getter の実装は動的に使用可能になりませんでした。 このエラーは、次の 2 つの方法のいずれかを使用して修正できます。  
  
- [\<Type](type-element-net-native.md) 要素で `Book` 型の `Dynamic` ポリシーを定義する。  
  
- 次の default.rd.xml ファイルのように、呼び出す getter を持つ各プロパティに入れ子になった [\<Property>](property-element-net-native.md) 要素を追加する。  
  
    ```xml  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
       <Application>  
          <Namespace Name="LibraryApplications"  Browse="Required Public" >  
             <Type Name="Book"   Activate="All" >  
                <Property Name="Title" Dynamic="Required" />  
                <Property Name="Author" Dynamic="Required" />  
                  <Property Name="ISBN" Dynamic="Required" />  
             </Type>  
          </Namespace>  
       </Application>  
    </Directives>  
    ```  
  
## <a name="see-also"></a>関連項目

- [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](runtime-directives-rd-xml-configuration-file-reference.md)
- [ランタイム ディレクティブ要素](runtime-directive-elements.md)
- [ランタイム ディレクティブ ポリシーの設定](runtime-directive-policy-settings.md)
