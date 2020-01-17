---
title: 依存関係プロパティ
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: bd12d05dbba133503778e6df3cd0e6c3e5689d5b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709492"
---
# <a name="dependency-properties"></a>依存関係プロパティ
依存関係プロパティ (DP) は、など、型の変数 (field) に格納するのではなく、プロパティストアにその値を格納する通常のプロパティです。  
  
 アタッチされた依存関係プロパティは、静的な Get メソッドと Set メソッドとしてモデル化された依存関係プロパティの一種で、オブジェクトとそのコンテナーの間のリレーションシップ (`Panel` コンテナー上の `Button` オブジェクトの位置など) を示す "プロパティ" を表します。  
  
 **✓ DO** プロパティ スタイル設定、トリガー、データ バインディング、アニメーション、動的なリソース、および継承などの WPF 機能をサポートする必要がある場合は、依存関係プロパティを提供します。  
  
## <a name="dependency-property-design"></a>依存関係プロパティのデザイン  
 **✓ DO** から継承<xref:System.Windows.DependencyObject>、または依存関係プロパティを実装する場合、そのサブタイプのいずれか。 型は、プロパティストアの非常に効率的な実装を提供し、WPF のデータバインディングを自動的にサポートします。  
  
 **✓ DO** 正規の CLR プロパティとパブリックな静的読み取り専用フィールドのインスタンスを格納する提供<xref:System.Windows.DependencyProperty?displayProperty=nameWithType>各依存関係プロパティです。  
  
 **✓ DO** 依存関係プロパティを実装するインスタンス メソッドを呼び出すことによって<xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType>と<xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>です。  
  
 **✓ DO** "Property"のプロパティの名前をアスタリスクの依存関係プロパティの静的フィールドの名前  
  
 **X DO NOT** コード内の依存関係プロパティの既定値を明示的に設定を代わりにメタデータの設定です。  
  
 プロパティの既定値を明示的に設定した場合、スタイル設定などのいくつかの暗黙的な方法によってそのプロパティが設定されないようにすることができます。  
  
 **X DO NOT** 静的フィールドにアクセスする標準コード以外のプロパティ アクセサーにコードを配置します。  
  
 スタイル設定などの暗黙的な方法によってプロパティが設定されている場合、そのコードは実行されません。これは、スタイルが静的フィールドを直接使用するためです。  
  
 **X DO NOT** 依存関係プロパティを使用してセキュリティで保護されたデータを格納します。 プライベート依存関係プロパティも、パブリックにアクセスできます。  
  
## <a name="attached-dependency-property-design"></a>アタッチされた依存関係プロパティのデザイン  
 前のセクションで説明した依存関係プロパティは、宣言する型の組み込みプロパティを表します。たとえば、`Text` プロパティは `TextButton`のプロパティであり、これを宣言します。 特別な種類の依存関係プロパティは、アタッチされる依存関係プロパティです。  
  
 添付プロパティの典型的な例は、<xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> プロパティです。 プロパティは、ボタンの (グリッドではなく) 列の位置を表しますが、グリッドにボタンが含まれている場合にのみ関連し、グリッドによってボタンに "アタッチ" されます。  
  
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
  
 添付プロパティの定義は、通常の依存関係プロパティとほとんど同じように見えますが、アクセサーは静的な Get メソッドと Set メソッドによって表される点が異なります。  
  
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
 プロパティは、多くの場合、検証と呼ばれるものを実装します。 検証ロジックは、プロパティの値を変更しようとしたときに実行されます。  
  
 残念ながら、依存関係プロパティのアクセサーに任意の検証コードを含めることはできません。 代わりに、プロパティの登録時に依存関係プロパティの検証ロジックを指定する必要があります。  
  
 **X DO NOT** プロパティのアクセサーの依存関係プロパティの検証ロジックを配置します。 代わりに、検証コールバックを `DependencyProperty.Register` メソッドに渡します。  
  
## <a name="dependency-property-change-notifications"></a>依存関係プロパティの変更通知  
 **X DO NOT** 依存関係プロパティのアクセサーでの変更通知のロジックを実装します。 依存関係プロパティには、変更通知コールバックを <xref:System.Windows.PropertyMetadata>に提供することによって使用する必要がある、組み込みの変更通知機能があります。  
  
## <a name="dependency-property-value-coercion"></a>依存関係プロパティ値の強制変換  
 プロパティの強制変換は、プロパティの set アクセス操作子に渡された値が setter によって変更されたときに、プロパティストアが実際に変更される前に行われます。  
  
 **X DO NOT** 依存関係プロパティのアクセサーに強制変換ロジックを実装します。  
  
 依存関係プロパティには組み込みの強制型変換機能があり、強制実行コールバックを `PropertyMetadata`に渡すことによって使用できます。  
  
 *©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*  
  
 *2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [共通デザイン パターン](../../../docs/standard/design-guidelines/common-design-patterns.md)
