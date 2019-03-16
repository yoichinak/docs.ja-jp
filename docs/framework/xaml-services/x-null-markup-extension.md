---
title: x:Null のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- NullExtension
- x:NullExtension
- x:Null
- "Null"
- xNull
helpviewer_keywords:
- Null markup extension in XAML [XAML Services]
- x:Null markup extension [XAML Services]
- XAML [XAML Services], x:Null markup extension
ms.assetid: 2e3ccc21-4996-481d-91b5-3910d8b3bfa3
ms.openlocfilehash: 34a2de71bec9b0929070aa908741de38b5904643
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/15/2019
ms.locfileid: "58029363"
---
# <a name="xnull-markup-extension"></a>x:Null のマークアップ拡張機能
指定します`null`XAML メンバーの値として。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Remarks  
 Null 参照のキーワードC#と[!INCLUDE[TLA#tla_cpp](../../../includes/tlasharptla-cpp-md.md)]が null です。 Null 参照の Microsoft Visual Basic のキーワードは、 `Nothing`、常に使用するが、`{x:Null}`として XAML 使用量に関係なく、XAML と関連付けた分離コード言語。  
  
 `x:Null`マークアップ拡張機能には、設定可能なプロパティがありません。  
  
 Null の使用は、CLR の XAML メンバーの露出を関連付け、<xref:System.Nullable%601>値。  
  
 `x:Null`マークアップ拡張機能のすべての XAML マークアップ拡張機能のように、中かっこを使用して (`{,}`) 以外のリテラルまたはイベント ハンドラーの参照属性の値の処理をエスケープします。 属性構文は、このマークアップ拡張機能で最もよく使用される構文です。 オブジェクト要素構文`<x:Null />`は技術的には可能ですが、あまり使われないため、`x:Null`マークアップ拡張機能には、位置指定パラメーターまたは構築引数がありません。  
  
 マークアップ拡張機能については、次を参照してください。[マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)します。  
  
 このマークアップ拡張機能の処理がによって定義されている .NET Framework XAML サービスを<xref:System.Windows.Markup.NullExtension>クラス。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 なお`null`参照型の依存関係プロパティの初期設定されていない値とは限りません。 既定の初期値は、依存関係プロパティごとに異なることができ、プロパティ固有のメタデータに基づくことができます。 多くの依存関係プロパティが受け入れない`null`マークアップまたはコードの検証コールバックの実装のための値として。 依存関係プロパティの詳細については、次を参照してください。[依存関係プロパティの概要](../wpf/advanced/dependency-properties-overview.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML の概要 (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
