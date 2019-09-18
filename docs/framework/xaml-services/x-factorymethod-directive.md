---
title: x:FactoryMethod ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- XAML. x:FactoryMethod directive [XAML Services]
- FactoryMethod directive in XAML [XAML Services]
- x:FactoryMethod directive [XAML Services]
ms.assetid: 829bcbdf-5318-4afb-9a03-c310e0d2f23d
ms.openlocfilehash: 586965dd4094e81fd830a09b64604cf33f195630
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053775"
---
# <a name="xfactorymethod-directive"></a>x:FactoryMethod ディレクティブ
バッキング型を解決した後に、XAML プロセッサがオブジェクトを初期化するために使用する必要があるコンストラクター以外のメソッドを指定します。  
  
## <a name="xaml-attribute-usage-no-xarguments"></a>XAML 属性の使用、x:Arguments なし  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-attribute-usage-xarguments-as-elements"></a>XAML 属性の使用法、x:Arguments as 要素  
  
```xaml  
<object x:FactoryMethod="methodname"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`methodname`|として`object`指定されたインスタンスを初期化するために XAML プロセッサが呼び出すメソッドの文字列メソッド名。 「解説」を参照してください。|  
|`oneOrMoreObjectElements`|ファクトリメソッドのパラメーターを指定するオブジェクトの1つ以上のオブジェクト要素。 順序は重要です。これは、引数をファクトリメソッドに渡す順序を示します。|  
  
## <a name="remarks"></a>Remarks  
 が`methodname`インスタンスメソッドの場合、修飾することはできません。  
  
 ファクトリメソッドとしての静的メソッドがサポートされています。 が`methodname`静的メソッドの場合、 `methodname`は*typeName*として指定されます。*methodName*の組み合わせ。ここで、 *typeName*は、静的ファクトリメソッドを定義するクラスに名前を指定します。 マップされた xmlns 内の型を参照する場合は、 *typeName*をプレフィックスで修飾できます。 *typeName*は、とは異なる型`typeof(object)`にすることができます。  
  
 ファクトリメソッドは、関連するオブジェクト要素をバッキングする型の宣言されたパブリックメソッドである必要があります。  
  
 ファクトリメソッドは、関連するオブジェクトに割り当て可能なインスタンスを返す必要があります。 ファクトリメソッドは null を返すことはできません。  
  
 `x:Arguments`ファクトリメソッドのシグネチャに最適な原則を使用して動作します。 照合では、最初にパラメーター数が評価されます。 パラメーターの数に一致する候補が複数ある場合は、パラメーターの型が評価され、最適な一致が決定されます。 この評価フェーズの後もあいまいさが残っている場合、XAML プロセッサの動作は未定義です。  
  
 一般的な意味では、要素の使用法はプロパティ要素の使用ではありません。これは、ディレクティブマークアップが、包含するオブジェクト要素の型を参照しないためです。`x:FactoryMethod` 要素の使用法が属性の使用法よりも低いことが想定されています。 `x:Arguments`(属性または要素の使用法) を要素の`x:FactoryMethod`使用法と共に使用できますが、これは使用方法のセクションでは特に示されていません。  
  
 `x:FactoryMethod`要素は他のプロパティ要素の前に置く必要がある`x:Arguments`ため、は要素として指定されたの前に記述する必要があり、コンテンツ/内部テキスト/初期化テキストの前に記述する必要があります。  
  
## <a name="see-also"></a>関連項目

- [x:Arguments ディレクティブ](x-arguments-directive.md)
