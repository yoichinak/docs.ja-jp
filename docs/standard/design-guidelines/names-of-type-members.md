---
title: 型のメンバーの名前
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- events [.NET Framework], names
- methods [.NET Framework], names
- type members
- properties [.NET Framework], names
- fields, names
- field names
- names [.NET Framework], type members
- members [.NET Framework], type
ms.assetid: af5a0903-36af-4c2a-b848-cf959affeaa5
author: KrzysztofCwalina
ms.openlocfilehash: b4da14575d29582814d32a3050087b7acc0da802
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353704"
---
# <a name="names-of-type-members"></a>型のメンバーの名前
型は次のメンバーで構成されています: メソッド、プロパティ、イベント、コンストラクター、フィールド。 次のセクションは、型のメンバーに名前を付けるためのガイドラインを示しています。  
  
## <a name="names-of-methods"></a>メソッドの名前  
 メソッドはアクションを実行する手段であるため、デザインのガイドラインでは、メソッド名を動詞または動詞句にする必要があります。 また、このガイドラインに従うと、名詞句または形容詞句であるプロパティ名および型名と、メソッド名を区別するためにも機能します。  
  
 **✓ DO** 動詞または動詞句は、メソッドの名前を指定します。  
  
```csharp  
public class String {  
    public int CompareTo(...);  
    public string[] Split(...);  
    public string Trim();  
}  
```  
  
## <a name="names-of-properties"></a>プロパティの名前  
 他のメンバーとは異なり、プロパティには名詞句または形容詞の名前を指定する必要があります。 つまり、プロパティはデータを参照するため、プロパティの名前にはデータが反映されます。 プロパティ名には、常に Pascal 形式が使用されます。  
  
 **✓ DO** 名詞、名詞句、または形容詞を使用してプロパティの名前を付けます。  
  
 **X DO NOT** 次の例のように、"Get"メソッドの名前に一致するプロパティがあります。  
  
 `public string TextWriter { get {...} set {...} }`  
 `public string GetTextWriter(int value) { ... }`  
  
 通常、このパターンは、プロパティが実際にメソッドであることを示します。  
  
 **✓ DO** 後に"List"または"Collection"単数形の語句を使用する代わりに、コレクション内の項目を記述する複数形の語句でコレクションのプロパティの名前を付けます  
  
 **✓ DO** 肯定の語句でブール型プロパティの名前 (`CanSeek`の代わりに`CantSeek`)。 必要に応じて、ブールプロパティの先頭に "Is"、 "Can"、または "Has"を追加することもできますが、値を追加する場合に限定します。  
  
 **✓ CONSIDER** プロパティの型と同じ名前を提供します。  
  
 たとえば、次のプロパティは、`Color` という名前の列挙値を適切に取得および設定するため、プロパティは `Color` という名前になります。  
  
```csharp  
public enum Color {...}  
public class Control {  
    public Color Color { get {...} set {...} }  
}  
```  
  
## <a name="names-of-events"></a>イベントの名前  
 イベントは常に、発生中のアクションまたは発生したアクションのいずれかのアクションを参照します。 そのため、メソッドと同様、イベントには動詞の名前が付けられ、イベントが発生した時刻を示すために動詞の時制が使用されます。  
  
 **✓ DO** 動詞または動詞句を持つイベントの名前を付けます。  
  
 例として、`Clicked`、`Painting`、`DroppedDown` などがあります。  
  
 **✓ DO** 現在および過去時制を使用して、前後の概念でイベント名を提供します。  
  
 たとえば、ウィンドウを閉じる前に発生するクローズ イベントは `Closing` と呼ばれ、ウィンドウを閉じた後に発生するクローズ イベントは `Closed` と呼ばれます。  
  
 **X DO NOT** プレイベントとポストイベントを示す "Before" または "After"を接頭や接尾に使用しないでください。 前述の通り、現在と過去の時制を使用します。 前述のように、現在形と過去形を使用します。  
  
 **✓ DO** 次の例に示すように"EventHandler"サフィックスを持つイベント ハンドラー (デリゲートがイベントの種類として使用) の名前をつけます。  
  
 `public delegate void ClickedEventHandler(object sender, ClickedEventArgs e);`  
  
 **✓ DO** イベント ハンドラーにおいては`sender`と`e`という 2 つのパラメーターを使用します。  
  
 sender パラメーターは、イベントを発生させたオブジェクトを表します。 より具体的な型を使用できる場合も、通常、sender パラメーターの型は `object` になります。  
  
 **✓ DO** イベント引数クラス"EventArgs"サフィックスを持つ名前を付けます。  
  
## <a name="names-of-fields"></a>フィールドの名前  
 フィールドの名前付けのガイドラインは、静的パブリック フィールドと保護されたフィールドを対象とします。 内部フィールドとプライベート フィールドは、ガイドラインの対象ではありません。また、パブリック インスタンス フィールドや保護されたインスタンス フィールドは、「[メンバーのデザインのガイドライン](../../../docs/standard/design-guidelines/member.md)」で許可されていません。  
  
 **✓ DO** フィールドの名前に PascalCasing を使用します。  
  
 **✓ DO** 名詞、名詞句、または形容詞を使用してフィールドの名前を付けます。  
  
 **X DO NOT** フィールド名に接頭語を使用しないでください。  
  
 たとえば、静的フィールドを示すために、"g_" や "s_" を使用しないでください。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 [ Framework のデザインガイドラインから、ピアソン教育, Inc. のアクセス許可によって @no__t。再利用可能な .NET ライブラリの規則、表現、パターン、2番目のエディション @ no__t-0 by Krzysztof Cwalina、および Addison-Wesley Professional によって Microsoft Windows 開発シリーズの一部として2008年10月22日に公開さ @no__t れました。  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
