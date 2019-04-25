---
title: PresentationOptions:Freeze 属性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: e60c4a505db42936f188354f52edd7832fb9632b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074665"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze 属性
セット、<xref:System.Windows.Freezable.IsFrozen%2A>状態`true`で格納している<xref:System.Windows.Freezable>要素。 既定の動作を<xref:System.Windows.Freezable>せず、`PresentationOptions:Freeze`属性が指定される<xref:System.Windows.Freezable.IsFrozen%2A>は`false`の読み込み時間、および [全般] に依存<xref:System.Windows.Freezable>時の動作。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```  
<object  
  xmlns:PresentationOptions="http://schemas.microsoft.com/winfx/2006/xaml/presentation/options"  
  xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
  mc:Ignorable="PresentationOptions">  
    <freezableElement PresentationOptions:Freeze="true"/>  
</object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`PresentationOptions`|XML 1.0 仕様に従って、任意の有効なプレフィックス文字列を指定できる XML 名前空間プレフィックス。 プレフィックス`PresentationOptions`はこのドキュメントでの識別目的で使用します。|  
|`freezableElement`|いずれかをインスタンス化する要素のクラスを派生する<xref:System.Windows.Freezable>します。|  
  
## <a name="remarks"></a>Remarks  
 `Freeze`属性は、唯一の属性またはその他のプログラミング要素で定義されて、 `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 名前空間。 `Freeze` Ignorable としてを使用して、指定することができますように具体的には、この特別な名前空間の属性が存在する[mc: Ignorable 属性](mc-ignorable-attribute.md)ルート要素の宣言の一部として。 理由を`Freeze`が無視できる必要がありますでないため、すべて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装に固定することは、<xref:System.Windows.Freezable>ロード時にこの機能はありませんの一部、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]仕様。  
  
 処理する機能、`Freeze`属性は、具体的に組み込まれている、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]処理プロセッサ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]用にコンパイルされたアプリケーション。 属性は、任意のクラスでサポートされていないと、属性構文が拡張または変更します。 独自に実装している場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの固定動作することもできます、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの処理時に、`Freeze`属性<xref:System.Windows.Freezable>の読み込み時に要素。  
  
 任意の値、`Freeze`以外の属性`true`(いない大文字小文字を区別)、負荷時のエラーが生成されます。 (を指定する、`Freeze`属性として`false`、エラーではありませんが、既定値設定するためにはない`false`は何も行いません)。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Freezable>
- [Freezable オブジェクトの概要](freezable-objects-overview.md)
- [mc:Ignorable 属性](mc-ignorable-attribute.md)
