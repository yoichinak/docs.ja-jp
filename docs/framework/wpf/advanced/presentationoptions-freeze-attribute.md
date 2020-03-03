---
title: PresentationOptions:Freeze 属性
ms.date: 03/30/2017
helpviewer_keywords:
- Freeze attribute [WPF]
- Freezable elements [WPF]
- PresentationOptions prefix [WPF]
ms.assetid: 391032dd-2fba-4804-bb8a-3b071797a9f4
ms.openlocfilehash: d3e0cee293a9585b972b0145da953976ed94b74c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991421"
---
# <a name="presentationoptionsfreeze-attribute"></a>PresentationOptions:Freeze 属性
`true` <xref:System.Windows.Freezable.IsFrozen%2A> 親<xref:System.Windows.Freezable>要素の状態をに設定します。 `PresentationOptions:Freeze` <xref:System.Windows.Freezable.IsFrozen%2A> 属性が指定さ<xref:System.Windows.Freezable>れてい<xref:System.Windows.Freezable>ないの既定の動作では、読み込み時にが実行時の一般的な動作に依存します。`false`  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
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
|`PresentationOptions`|Xml 1.0 の仕様に従って、任意の有効なプレフィックス文字列を指定できる XML 名前空間プレフィックス。 このドキュメント`PresentationOptions`では、識別のためにプレフィックスが使用されます。|  
|`freezableElement`|の<xref:System.Windows.Freezable>派生クラスをインスタンス化する要素。|  
  
## <a name="remarks"></a>Remarks  
 属性は、 `http://schemas.microsoft.com/winfx/2006/xaml/presentation/options` XML 名前空間で定義されている唯一の属性またはその他のプログラミング要素です。 `Freeze` 属性`Freeze`は、ルート要素宣言の一部として[mc: ignorable 属性](mc-ignorable-attribute.md)を使用して、無視可能として指定できるように、この特別な名前空間に存在します。 が無視できる`Freeze`理由は、すべて[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のプロセッサ実装が読み込み時にを<xref:System.Windows.Freezable>フリーズできるわけではないためです。この機能は[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]仕様の一部ではありません。  
  
 `Freeze`属性を処理する機能は、コンパイルされたアプリケーション[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のを処理[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]するプロセッサに特に組み込まれています。 属性はどのクラスでもサポートされていません。また、属性の構文は拡張または変更できません。 独自[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のプロセッサを実装する場合は、読み込み時に<xref:System.Windows.Freezable>要素の`Freeze`属性を処理[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]するときに、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサのフリーズ動作を並列処理することを選択できます。  
  
 `Freeze` 以外`true`の属性の値 (大文字と小文字は区別されません) は、読み込み時間エラーを生成します。 ( `Freeze`属性をとし`false`て指定するのはエラーではなく、既に既定値で`false`あるため、をに設定することはできません)。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Freezable>
- [Freezable オブジェクトの概要](freezable-objects-overview.md)
- [mc:Ignorable 属性](mc-ignorable-attribute.md)
