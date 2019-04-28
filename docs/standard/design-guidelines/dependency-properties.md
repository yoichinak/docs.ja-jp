---
title: 依存関係プロパティ
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
author: KrzysztofCwalina
ms.openlocfilehash: 52d7a69a3f52c67ebff3f3db1daf0790e995913a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778769"
---
# <a name="dependency-properties"></a>依存関係プロパティ
依存関係プロパティ (DP) は、たとえば (フィールド) の型の変数に格納することではなく、プロパティ ストアにその値を格納する標準プロパティです。  
  
 依存プロパティは、ある種のオブジェクトとそのコンテナーの間のリレーションシップを記述する「プロパティ」を表す、Get と Set の静的メソッドとしてモデル化された依存関係プロパティ (の位置など、`Button`上のオブジェクトを`Panel`コンテナーの場合)。  
  
 **✓ DO** プロパティ スタイル設定、トリガー、データ バインディング、アニメーション、動的なリソース、および継承などの WPF 機能をサポートする必要がある場合は、依存関係プロパティを提供します。  
  
## <a name="dependency-property-design"></a>依存関係プロパティのデザイン  
 **✓ DO** から継承<xref:System.Windows.DependencyObject>、または依存関係プロパティを実装する場合、そのサブタイプのいずれか。 型は、プロパティ ストアの非常に効率的な実装を提供し、自動的に WPF データ バインドをサポートします。  
  
 **✓ DO** 正規の CLR プロパティとパブリックな静的読み取り専用フィールドのインスタンスを格納する提供<xref:System.Windows.DependencyProperty?displayProperty=nameWithType>各依存関係プロパティです。  
  
 **✓ DO** 依存関係プロパティを実装するインスタンス メソッドを呼び出すことによって<xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType>と<xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>です。  
  
 **✓ DO** "Property"のプロパティの名前をアスタリスクの依存関係プロパティの静的フィールドの名前  
  
 **X DO NOT** コード内の依存関係プロパティの既定値を明示的に設定を代わりにメタデータの設定です。  
  
 プロパティの既定値を明示的に設定するをスタイル設定などのいくつかの暗黙的な方法で設定されているから、そのプロパティをできない場合があります。  
  
 **X DO NOT** 静的フィールドにアクセスする標準コード以外のプロパティ アクセサーにコードを配置します。  
  
 コードがしません実行をスタイル設定などの暗黙的な方法で、プロパティが設定されている場合のスタイルを設定するため、静的フィールドを直接使用します。  
  
 **X DO NOT** 依存関係プロパティを使用してセキュリティで保護されたデータを格納します。 プライベートでも依存関係プロパティは、パブリックにアクセスできます。  
  
## <a name="attached-dependency-property-design"></a>接続されている依存関係プロパティのデザイン  
 依存関係プロパティが、前のセクションで説明されている宣言型の組み込みのプロパティを表しますたとえば、`Text`プロパティは、プロパティの`TextButton`、宣言します。 依存関係プロパティの特殊なは、接続されている依存関係プロパティです。  
  
 添付プロパティの典型的な例は、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType>プロパティ。 プロパティ ボタン (いないグリッドの) 列の位置を表しますは"にアタッチされている"ボタンのグリッドで、グリッドで、ボタンが含まれている場合にのみ関連します。  
  
```xaml
<Grid>  
    <Grid.ColumnDefinitions>  
        <ColumnDefinition />  
        <ColumnDefinition />  
    </Grid.ColumnDefinitions>  
  
    <Button Grid.Column="0">Click</Button>  
    <Button Grid.Column="1">Clack</Button>  
</Grid>  
```  
  
 添付プロパティの定義は、アクセサーが静的な Get と Set メソッドによって表されることを除いて、通常の依存関係プロパティのほとんどの場合ようになります。  
  
```csharp
public class Grid {  
  
    public static int GetColumn(DependencyObject obj) {  
        return (int)obj.GetValue(ColumnProperty);  
    }  
  
    public static void SetColumn(DependencyObject obj, int value) {  
        obj.SetValue(ColumnProperty,value);  
    }  
  
    public static readonly DependencyProperty ColumnProperty =  
        DependencyProperty.RegisterAttached(  
            "Column",  
            typeof(int),  
            typeof(Grid)  
    );  
}  
```  
  
## <a name="dependency-property-validation"></a>依存関係プロパティの検証  
 プロパティは、多くの場合、検証と呼ばれるものを実装します。 プロパティの値を変更する試行したときに検証ロジックを実行します。  
  
 残念なことに依存関係プロパティのアクセサーには、任意の検証コードを含めることはできません。 代わりに、依存関係プロパティの検証ロジックは、プロパティの登録時に指定する必要があります。  
  
 **X DO NOT** プロパティのアクセサーの依存関係プロパティの検証ロジックを配置します。 代わりに、検証コールバックを渡す`DependencyProperty.Register`メソッド。  
  
## <a name="dependency-property-change-notifications"></a>依存関係プロパティの変更通知  
 **X DO NOT** 依存関係プロパティのアクセサーでの変更通知のロジックを実装します。 依存関係プロパティに変更通知のコールバックを指定して使用する必要があります組み込みの変更通知機能があり、<xref:System.Windows.PropertyMetadata>します。  
  
## <a name="dependency-property-value-coercion"></a>依存関係プロパティの値の強制型変換  
 プロパティ ストアが実際に変更する前に、setter をプロパティ set アクセス操作子に渡された値が変更されたときにプロパティの強制型変換が行われます。  
  
 **X DO NOT** 依存関係プロパティのアクセサーに強制変換ロジックを実装します。  
  
 依存関係プロパティは、組み込みの強制型変換機能を持っているし、強制型変換のコールバックを指定することによって使用できます、`PropertyMetadata`します。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [共通デザイン パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)
