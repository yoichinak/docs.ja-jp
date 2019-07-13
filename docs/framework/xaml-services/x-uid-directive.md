---
title: x:Uid ディレクティブ
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: c8f0580c987b87193b5b6a38559043e50fc7cb89
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938841"
---
# <a name="xuid-directive"></a>x:Uid ディレクティブ
マークアップ要素の一意の識別子を提供します。 多くのシナリオでは、この一意の識別子は XAML のローカライズ プロセスとツールによって使用されます。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`identifier`|手動で作成または自動生成された文字列を指定する必要がありますで一意であるファイルによって解釈されるは、その場合、`x:Uid`コンシューマー。|  
  
## <a name="remarks"></a>Remarks  
 MS-XAML で`x:Uid`ディレクティブとして定義されます。 詳細については、次を参照してください。 [ \[MS XAML\]セクション 5.3.6](https://go.microsoft.com/fwlink/?LinkId=114525)します。  
  
 `x:Uid` 不連続`x:Name`両方規定された XAML のローカライズ シナリオのため、ローカライズに使用される識別子のプログラミング モデルの結果に対する依存関係があるないように`x:Name`。 また、`x:Name`は規定された XAML 名前スコープ。 ただし、`x:Uid`一意性の強制の XAML 定義されている言語概念によって制御されていません。 XAML プロセッサは広い意味 (プロセッサ、ローカライズ プロセスの一部ではない) では、一意性を適用する必要はありません`x:Uid`値。 その責任は元の値には、概念的には。 一意性のことを期待`x:Uid`1 つの XAML ソース内の値は、値は、専用のグローバル化のプロセスやツールなどのコンシューマーに適しています。 一意性の一般的なモデルは`x:Uid`値は、XAML を表す XML でエンコードされたファイル内で一意です。  
  
 適用する特定の XAML スキーマの重要な情報を持っているツールを選択できます`x:Uid`のみでテキストの文字列値がマークアップでが発生したすべてのケースについての代わりに、ローカライズ可能な文字列を true です。  
  
 フレームワークは、エイリアスにするには、そのオブジェクト モデルで特定のプロパティを指定できます`x:Uid`属性を適用することで<xref:System.Windows.Markup.UidPropertyAttribute>を定義する型。 フレームワークでは、特定のプロパティを指定する場合は、両方を指定する有効ないない`x:Uid`と同じオブジェクトの別名のメンバー。 両方`x:Uid`エイリアス化されたメンバーを指定すると、通常 .NET Framework XAML サービス API をスローおよび<xref:System.Xaml.XamlDuplicateMemberException>このケース。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 ロールの詳細については`x:Uid`WPF のローカライズ プロセスおよび XAML の BAML 形式では、「 [WPF のグローバリゼーション](../wpf/advanced/globalization-for-wpf.md)または <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [WPF のグローバリゼーション](../wpf/advanced/globalization-for-wpf.md)
