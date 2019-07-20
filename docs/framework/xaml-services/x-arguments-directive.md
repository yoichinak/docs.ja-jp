---
title: x:Arguments ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 5bcd629e306169c1f7a61a316d76203827a2d0fe
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364271"
---
# <a name="xarguments-directive"></a>x:Arguments ディレクティブ
XAML でのパラメーターなしのコンストラクターオブジェクト要素の宣言またはファクトリメソッドオブジェクトの宣言に対する構築引数をパッケージ化します。  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>XAML 要素の使用法 (パラメーターなしのコンストラクター)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML 要素の使用法 (ファクトリメソッド)  
  
```  
<object x:FactoryMethod="methodName"...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`oneOrMoreObjectElements`|バッキングでないパラメーターなしのコンストラクターまたはファクトリメソッドに渡される引数を指定する1つ以上のオブジェクト要素。<br /><br /> 一般的な使用方法は、オブジェクト要素内で初期化テキストを使用して、実際の引数値を指定することです。 「例」セクションを参照してください。<br /><br /> 要素の順序は重要です。 順序の XAML 型は、バッキングコンストラクターまたはファクトリメソッドのオーバーロードの型および型の順序と一致する必要があります。|  
|`methodName`|任意`x:Arguments`の引数を処理するファクトリメソッドの名前。|  
  
## <a name="dependencies"></a>依存関係  
 `x:FactoryMethod`適用される`x:Arguments`スコープと動作を変更できます。  
  
 が指定`x:FactoryMethod`されて`x:Arguments`いない場合、はバッキングコンストラクターの別の (既定ではない) シグネチャに適用されます。  
  
 を`x:FactoryMethod`指定した`x:Arguments`場合、は名前付きメソッドのオーバーロードに適用されます。  
  
## <a name="remarks"></a>Remarks  
 XAML 2006 では、初期化テキストによる既定以外の初期化をサポートできます。 ただし、初期化テキストの構築手法の実際の応用は限られています。 初期化テキストは1つのテキスト文字列として扱われます。したがって、カスタム情報項目やカスタムの区切り記号を文字列から解析できる構築動作に対して型コンバーターが定義されていない限り、1つのパラメーター初期化の機能が追加されるだけです。 また、オブジェクトロジックへのテキスト文字列は、実際の文字列以外のプリミティブを処理するために、特定の XAML パーサーのネイティブの既定の型コンバーターである可能性があります。  
  
 XAML `x:Arguments`の使用法は、一般的な意味ではプロパティ要素の使用法ではありません。これは、ディレクティブマークアップが、包含するオブジェクト要素の型を参照しないためです。 これは、要素が子コンテンツの既定`x:Code`値以外としてマークアップを解釈する必要がある範囲を要素がどのようにマークするかなど、他のディレクティブに似ています。 この場合、各オブジェクト要素の xaml 型は、引数の型に関する情報を伝達します。これは、xaml パーサーによって使用され`x:Arguments` 、使用されている特定のコンストラクターファクトリメソッドシグネチャのうち、どのコンストラクターが参照しようとしているかを判断するために使用されます。  
  
 `x:Arguments`構築するオブジェクト要素は、他のプロパティ要素、コンテンツ、内部テキスト、またはオブジェクト要素の初期化文字列の前に記述する必要があります。 内`x:Arguments`のオブジェクト要素には、その XAML 型およびそのバッキングコンストラクターまたはファクトリメソッドで許可されている属性と初期化文字列を含めることができます。 オブジェクトまたは引数のいずれかに対して、確立されたプレフィックスマッピングを参照することによって、既定の XAML 名前空間の外部にあるカスタム XAML 型または XAML 型を指定できます。  
  
 XAML プロセッサは、次のガイドラインを使用して、で`x:Arguments`指定された引数を使用してオブジェクトを構築する方法を決定します。 を`x:FactoryMethod`指定した場合、情報は指定し`x:FactoryMethod`たと比較されます`x:FactoryMethod` (の値がメソッド名であり、名前付きメソッドにオーバーロードがあることに注意してください)。 が`x:FactoryMethod`指定されていない場合、情報は、オブジェクトのすべてのパブリックコンストラクターのオーバーロードのセットと比較されます。 次に、XAML 処理ロジックは、パラメーターの数を比較し、一致するアリティを持つオーバーロードを選択します。 複数の一致がある場合、XAML プロセッサは、指定されたオブジェクト要素の XAML 型に基づいて、パラメーターの型を比較する必要があります。 一致するものが1つ以上ある場合、XAML プロセッサの動作は未定義です。 `x:FactoryMethod`が指定されていてもメソッドを解決できない場合、XAML プロセッサは例外をスローする必要があります。  
  
 XAML 属性の使用`<x:Arguments>string</x:Arguments>`は技術的に可能です。 ただし、これは初期化テキストと型コンバーターを使用して実行できない機能を提供するものではなく、この構文を使用することは、XAML 2009 ファクトリメソッド機能の設計目的ではありません。  
  
## <a name="examples"></a>使用例  
 次の例は、パラメーターなしのコンストラクターシグネチャを示し、そのシグネチャに`x:Arguments`アクセスするの XAML 使用方法を示しています。  
  
```csharp  
public class Food {  
    private string _name;  
    private Int32 _calories;  
    public Food(string name, Int32 calories) {  
        _name=name;  
        _calories=calories;  
    }  
}  
```  
  
```xaml  
<my:Food>  
    <x:Arguments>  
        <x:String>Apple</x:String>  
        <x:Int32>150</x:Int32>  
    </x:Arguments>  
</my:Food>  
```  
  
 次の例では、ターゲットファクトリメソッドシグネチャを示し、その署名`x:Arguments`にアクセスするの XAML 使用方法を示します。  
  
```csharp  
public Food TryLookupFood(string name)  
{  
  switch (name) {  
    case "Apple": return new Food("Apple",150);  
    case "Chocolate": return new Food("Chocolate",200);  
    case "Cheese": return new Food("Cheese", 450);  
    default: {return new Food(name,0);  
  }  
}  
```  
  
```xaml  
<my:Food x:FactoryMethod="TryLookupFood">  
    <x:Arguments>  
        <x:String>Apple</x:String>  
    </x:Arguments>  
</my:Food>  
```  
  
## <a name="see-also"></a>関連項目

- [.NET Framework XAML サービスで使用するためのカスタム型の定義](defining-custom-types-for-use-with-net-framework-xaml-services.md)
- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
