---
title: x:FactoryMethod ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: cb78514540f5f44b07b1fdd16283d26c647a3ac4
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58034546"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod ディレクティブ
XAML プロセッサが、バッキング型を解決した後、オブジェクトを初期化するために使用するコンス トラクター以外の方法を指定します。  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML 属性使用状況、x: 引数なし  
  
```  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML 属性使用状況、個の要素として X:arguments  
  
```  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`methodname`|文字列のメソッド名として指定されたインスタンスを初期化するために XAML プロセッサが呼び出すメソッドの`object`します。 「解説」を参照してください。|  
|`oneOrMoreObjectElements`|ファクトリ メソッドのパラメーターを指定するオブジェクトのオブジェクトの要素の 1 つ以上 順序は重要です。ファクトリ メソッドに引数を渡す必要があります、順序のことを示します。|  
  
## <a name="remarks"></a>Remarks  
 場合`methodname`インスタンス メソッドを修飾することもできません。  
  
 ファクトリ メソッドとしての静的メソッドがサポートされています。 場合`methodname`静的メソッドでは、`methodname`として提供されて、 *typeName*.*methodName*の組み合わせを*typeName*静的ファクトリ メソッドを定義するクラスの名前します。 *typeName*マップされた xmlns 内の型を参照している場合のプレフィックスで修飾することができます。 *typeName*より異なる型を指定できます`typeof(object)`します。  
  
 ファクトリ メソッドは、関連するオブジェクトの要素をサポートする型の宣言されたパブリック メソッドである必要があります。  
  
 ファクトリ メソッドには、関連するオブジェクトに割り当てることができるインスタンスを返す必要があります。 ファクトリ メソッドには null を返すことはありません。  
  
 `x:Arguments` ファクトリ メソッドのシグネチャに最適なものの原則で動作します。 一致するパラメーターの数を最初に評価します。 パラメーターの数に一致する 1 つ以上の場合は、パラメーターの型は、評価と最適な一致を確認しが。 評価のこのフェーズの後にあいまいさが残る、XAML プロセッサの動作は未定義です。  
  
 `x:FactoryMethod`要素の使用方法で、一般的な意味では、プロパティ要素による使用できないためはディレクティブのマークアップは、親オブジェクト要素の型を参照していません。 要素の使用方法は、属性の使用方法よりは一般的です。 `x:Arguments` 組み合わせて (属性または要素のいずれかの使用法) を使用することができます`x:FactoryMethod`要素の使用方法が、これは具体的には表示されません、使用状況のセクションでします。  
  
 `x:FactoryMethod` 要素には、他のすべてのプロパティ要素が前に指定する必要がありますのいずれかの必要があります前`x:Arguments`も、要素として提供されており、任意の初期化/コンテンツ/内部のテキストのテキストの前にする必要があります。  
  
## <a name="see-also"></a>関連項目
- [x:Arguments ディレクティブ](x-arguments-directive.md)
