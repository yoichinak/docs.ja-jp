---
title: x:Arguments ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- x:Arguments directive [XAML Services]
- Arguments directive in XAML [XAML Services]
- XAML [XAML Services], x:Arguments directive
ms.assetid: 87cc10b0-b610-4025-b6b0-ab27ca27c92e
ms.openlocfilehash: 351974786b9f4748499279d29202e2051d9268fd
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58043329"
---
# <a name="xarguments-directive"></a>x:Arguments ディレクティブ
パッケージの構築の引数、XAML で既定以外のコンス トラクター オブジェクト要素の宣言またはファクトリ メソッドのオブジェクトの宣言。  
  
## <a name="xaml-element-usage-nondefault-constructor"></a>XAML 要素の使用 (既定以外のコンス トラクター)  
  
```  
<object ...>  
  <x:Arguments>  
    oneOrMoreObjectElements  
  </x:Arguments>  
</object>  
```  
  
## <a name="xaml-element-usage-factory-method"></a>XAML 要素の使用方法 (ファクトリ メソッド)  
  
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
|`oneOrMoreObjectElements`|既定以外のバッキング コンス トラクターまたはファクトリ メソッドに渡される引数を指定する 1 つまたは複数のオブジェクト要素。<br /><br /> 一般的な使用法では、実際の引数の値を指定するオブジェクトの要素内の初期化のテキストを使用します。 例のセクションをご覧ください。<br /><br /> 要素の順序は重要です。 順序内の XAML 型は、型と一致する必要があり、バッキング コンス トラクターまたはファクトリ メソッドのオーバー ロードの順序を入力します。|  
|`methodName`|いずれかを処理するファクトリ メソッドの名前`x:Arguments`引数。|  
  
## <a name="dependencies"></a>依存関係  
 `x:FactoryMethod` スコープと動作を変更することができます、`x:Arguments`適用されます。  
  
 ない場合は`x:FactoryMethod`が指定されている`x:Arguments`バッキング コンス トラクターの代替 (既定値) の署名に適用されます。  
  
 場合`x:FactoryMethod`が指定されている`x:Arguments`名前付きメソッドのオーバー ロードに適用されます。  
  
## <a name="remarks"></a>Remarks  
 XAML 2006 では、初期化のテキストを既定以外の初期化をサポートできます。 ただし、初期化テキストの構築方法の実用的なアプリケーションは制限されます。 初期化のテキストが 1 つのテキスト文字列として扱われますそのため、カスタム情報項目とカスタムの区切り記号文字列からを解析できる構築動作の型コンバーターが定義されていない場合、1 つのパラメーターの初期化の機能のみ追加します。 また、オブジェクトのロジックをテキスト文字列は、true 文字列以外のプリミティブを処理するための指定された XAML パーサーのネイティブの既定の型コンバーターでは可能性があります。  
  
 `x:Arguments` XAML の使用は、の一般的な意味で、プロパティ要素の使用方法、ディレクティブのマークアップが格納オブジェクト要素の型を参照していないためです。 など他のディレクティブと酷似`x:Code`要素境界の既定の子の内容以外に、マークアップを解釈する必要がありますの範囲を定めます。 ここでは、オブジェクトの各要素の XAML 型はどの特定のコンス トラクターのファクトリ メソッドのシグネチャを決定する XAML パーサーで使用される引数の型については、通信、`x:Arguments`参照しようとして使用します。  
  
 `x:Arguments` オブジェクト要素の構築される必要がありますの前に、その他のプロパティ要素、コンテンツ、内部テキ ストは、またはオブジェクトの要素の初期化の文字列。 内のオブジェクト要素`x:Arguments`その XAML の型とそのバッキングのコンス トラクターまたはファクトリ メソッドで許可されているように、属性と初期化文字列を含めることができます。 オブジェクトまたは引数のいずれかのカスタムの XAML 型または外部にあるそれ以外の場合、既定の XAML 名前空間によって確立されたプレフィックスのマッピングを参照する XAML 型を指定できます。  
  
 XAML プロセッサに引数を指定する方法を決定する、次のガイドラインを使用して`x:Arguments`オブジェクトを構築するために使用する必要があります。 場合`x:FactoryMethod`を指定すると、情報と比較を指定した`x:FactoryMethod`(注意の値`x:FactoryMethod`メソッドの名前し、名前付きメソッドのオーバー ロードを持つことができます。 場合`x:FactoryMethod`が指定されていない、情報は、オブジェクトのすべてのパブリック コンス トラクター オーバー ロードのセットと比較されます。 XAML 処理ロジックは、パラメーターの数を比較しと一致するアリティのオーバー ロードを選択します。 1 つ以上の一致がある場合、XAML プロセッサは提供されたオブジェクトの要素の XAML 型に基づいてパラメーターの型と比較します。 複数の一致がある場合、XAML プロセッサの動作は未定義です。 場合、`x:FactoryMethod`が指定されて、メソッドは、解決することはできませんは、XAML プロセッサは、例外をスローする必要があります。  
  
 XAML 属性の使用法`<x:Arguments>string</x:Arguments>`技術的に可能です。 ただし、この初期化のテキストと型コンバーターを使ってそれ以外の場合と行うことが含まれない機能はありません、この構文を使用して、XAML 2009 のファクトリ メソッドの機能の目的で設計ではありません。  
  
## <a name="examples"></a>使用例  
 次の例では、署名、次の XAML の使用状況は、既定以外のコンス トラクターを示しています`x:Arguments`その署名にアクセスします。  
  
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
  
 次の例では、ターゲット ファクトリ メソッドのシグネチャを次の XAML の使用状況を示しています。`x:Arguments`その署名にアクセスします。  
  
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
