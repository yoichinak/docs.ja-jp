---
title: x:Arguments ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 338286b417c78b7cceeb30188e888928a15607cd
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458655"
---
# <a name="xarguments-directive"></a>x:Arguments ディレクティブ
XAML でのパラメーターなしのコンストラクターオブジェクト要素の宣言またはファクトリメソッドオブジェクトの宣言に対する構築引数をパッケージ化します。  
  
## <a name="xaml-element-usage-nonparameterless-constructor"></a>XAML 要素の使用法 (パラメーターなしのコンストラクター)  
  
```xaml  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML 要素の使用法 (ファクトリメソッド)  
  
```xaml  
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
|`methodName`|`x:Arguments` の引数を処理するファクトリメソッドの名前。|  
  
## <a name="dependencies"></a>依存関係  
 `x:Arguments` 適用されるスコープと動作を変更 `x:FactoryMethod` ことができます。  
  
 `x:FactoryMethod` が指定されていない場合、`x:Arguments` バッキングコンストラクターの別の (既定ではない) シグネチャに適用されます。  
  
 `x:FactoryMethod` が指定されている場合、`x:Arguments` は名前付きメソッドのオーバーロードに適用されます。  
  
## <a name="remarks"></a>Remarks  
 XAML 2006 では、初期化テキストによる既定以外の初期化をサポートできます。 ただし、初期化テキストの構築手法の実際の応用は限られています。 初期化テキストは1つのテキスト文字列として扱われます。したがって、カスタム情報項目やカスタムの区切り記号を文字列から解析できる構築動作に対して型コンバーターが定義されていない限り、1つのパラメーター初期化の機能が追加されるだけです。 また、オブジェクトロジックへのテキスト文字列は、実際の文字列以外のプリミティブを処理するために、特定の XAML パーサーのネイティブの既定の型コンバーターである可能性があります。  
  
 XAML の使用法は、一般的な意味ではプロパティ要素の使用法ではありません。ディレクティブマークアップは、格納するオブジェクトの型を参照しないためです。 `x:Arguments` これは `x:Code` のような他のディレクティブに似ています。要素は、マークアップを子コンテンツの既定値以外として解釈する必要がある範囲を指定します。 この場合、各オブジェクト要素の XAML 型は、引数の型に関する情報を伝えます。これは、XAML パーサーによって使用され、`x:Arguments` 使用法が参照しようとしている特定のコンストラクターファクトリメソッドシグネチャを判別します。  
  
 構築されるオブジェクト要素の `x:Arguments` は、オブジェクト要素の他のプロパティ要素、コンテンツ、内部テキスト、または初期化文字列の前に記述する必要があります。 `x:Arguments` 内のオブジェクト要素には、その XAML 型およびそのバッキングコンストラクターまたはファクトリメソッドで許可されている属性と初期化文字列を含めることができます。 オブジェクトまたは引数のいずれかに対して、確立されたプレフィックスマッピングを参照することによって、既定の XAML 名前空間の外部にあるカスタム XAML 型または XAML 型を指定できます。  
  
 XAML プロセッサは、次のガイドラインを使用して、`x:Arguments` で指定された引数を使用してオブジェクトを構築する方法を決定します。 `x:FactoryMethod` が指定されている場合、情報は指定した `x:FactoryMethod` と比較されます (`x:FactoryMethod` の値がメソッド名であり、名前付きメソッドにオーバーロードがあることに注意してください。 `x:FactoryMethod` が指定されていない場合、情報はオブジェクトのすべてのパブリックコンストラクターのオーバーロードのセットと比較されます。 次に、XAML 処理ロジックは、パラメーターの数を比較し、一致するアリティを持つオーバーロードを選択します。 複数の一致がある場合、XAML プロセッサは、指定されたオブジェクト要素の XAML 型に基づいて、パラメーターの型を比較する必要があります。 一致するものが1つ以上ある場合、XAML プロセッサの動作は未定義です。 `x:FactoryMethod` が指定されていても、メソッドを解決できない場合、XAML プロセッサは例外をスローする必要があります。  
  
 XAML 属性の使用 `<x:Arguments>string</x:Arguments>` は、技術的には可能です。 ただし、これは初期化テキストと型コンバーターを使用して実行できない機能を提供するものではなく、この構文を使用することは、XAML 2009 ファクトリメソッド機能の設計目的ではありません。  
  
## <a name="examples"></a>使用例  
 次の例では、パラメーターなしのコンストラクターシグネチャを示し、そのシグネチャにアクセスする `x:Arguments` の XAML 使用方法を示します。  
  
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
  
 次の例では、ターゲットファクトリメソッドシグネチャを示し、その署名にアクセスする `x:Arguments` の XAML 使用方法を示します。  
  
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
- [XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
