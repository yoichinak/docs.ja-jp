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
ms.openlocfilehash: ff82b0bfc1983240431e582dbd78778dc4469241
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459937"
---
# <a name="xnull-markup-extension"></a>x:Null のマークアップ拡張機能
XAML メンバーの値として `null` を指定します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xaml  
<object property="{x:Null}" .../>  
```  
  
## <a name="remarks"></a>Remarks  
 およびC# C++内の null 参照のキーワードが null です。 Null 参照の Microsoft Visual Basic キーワードは `Nothing`ですが、XAML に関連付ける分離コード言語に関係なく、常に `{x:Null}` を XAML の使用として使用します。  
  
 `x:Null` マークアップ拡張機能には、設定可能なプロパティがありません。  
  
 Null 使用は、多くの場合、CLR <xref:System.Nullable%601> 値の XAML メンバー公開に関連付けられています。  
  
 すべての XAML マークアップ拡張機能と同様に、`x:Null` マークアップ拡張機能は、中かっこ (`{,}`) を使用して、リテラルまたはイベントハンドラー参照以外の属性値の処理をエスケープします。 属性構文は、このマークアップ拡張機能で最も頻繁に使用される構文です。 オブジェクト要素の構文 `<x:Null />` は技術的には可能ですが、`x:Null` マークアップ拡張機能に位置指定パラメーターも構築引数もないため、ほとんど使用されません。  
  
 マークアップ拡張機能の詳細については、「[マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)」を参照してください。  
  
 .NET Framework XAML サービスでは、このマークアップ拡張機能の処理は <xref:System.Windows.Markup.NullExtension> クラスによって定義されます。  
  
## <a name="wpf-usage-notes"></a>WPF の使用上の注意  
 `null` は、必ずしも参照型の依存関係プロパティの最初の未設定値ではないことに注意してください。 初期の既定値は、依存関係プロパティごとに異なる場合があり、プロパティ固有のメタデータに基づいている場合もあります。 多くの依存関係プロパティは、検証コールバックの実装により、マークアップまたはコードを使用して、`null` を値として受け入れません。 依存関係プロパティの詳細については、「[依存関係プロパティの概要](../wpf/advanced/dependency-properties-overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.DependencyProperty.UnsetValue>
- [XAML の概要 (WPF)](../../desktop-wpf/fundamentals/xaml.md)
- [マークアップ拡張機能と WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
