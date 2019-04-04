---
title: ThemeDictionary のマークアップ拡張機能
ms.date: 03/30/2017
f1_keywords:
- ThemeDictionaryExtension
- ThemeDictionary
helpviewer_keywords:
- ThemeDictionary markup extension [WPF]
- XAML [WPF], ThemeDictionary markup extension
ms.assetid: aa75e10b-13dd-4989-972d-51bab63a05e2
ms.openlocfilehash: 0bc4b2a11927bd2551dc322c5a856ade9a85c8b7
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364802"
---
# <a name="themedictionary-markup-extension"></a>ThemeDictionary のマークアップ拡張機能
カスタム コントロールの作成者またはアプリケーションでコントロールのスタイル設定を使用するテーマ固有のリソース ディクショナリの読み込みにサードパーティ製のコントロールを統合する方法を提供します。  
  
## <a name="xaml-attribute-usage"></a>XAML 属性の使用方法  
  
```xml  
<object property="{ThemeDictionary assemblyUri}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a>XAML オブジェクト要素の使用方法  
  
```xml  
<object>  
  <object.property>  
    <ThemeDictionary AssemblyName="assemblyUri"/>  
  <object.property>  
<object>  
```  
  
## <a name="xaml-values"></a>XAML 値  
  
|||  
|-|-|  
|`assemblyUri`|[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]のテーマ情報を格納するアセンブリ。 通常、これはより大きなパッケージ内のアセンブリを参照する uri です。 アセンブリのリソースとパッケージの Uri は、デプロイメントの問題を簡略化します。 詳細については、[WPF におけるパック Uri](../app-development/pack-uris-in-wpf.md)を参照してください。|  
  
## <a name="remarks"></a>Remarks  
 この拡張機能の目的は、1 つだけ特定のプロパティの値を入力する: の値を<xref:System.Windows.ResourceDictionary.Source%2A?displayProperty=nameWithType>します。  
  
 この拡張機能を使用すると、場合にのみを使用する一部のスタイルを含む 1 つのリソース専用のアセンブリを指定することができます、[!INCLUDE[TLA#tla_aero](../../../../includes/tlasharptla-aero-md.md)]テーマは、ユーザーのシステム、Luna テーマがアクティブ、ためには、その他のスタイルを適用します。 この拡張機能を使用すると、コントロール固有のリソース ディクショナリの内容に自動的に無効にできの必要な場合に別のテーマ固有のものを再読み込みします。  
  
 `assemblyUri`文字列 (<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>プロパティの値) の特定のテーマに適用するディクショナリを識別する名前付け規則の基礎が形成されます。 <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>ロジックを`ThemeDictionary`生成することによって、規則が完了すると、[!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)]プリコンパイル済みリソース アセンブリ内に含まれるように、特定のテーマ ディクショナリのバリアントを指します。 この規則、または一般的なコントロールのスタイルと概念としては、ページ/アプリケーション レベルのスタイルとテーマの相互作用を記述するについては、ここで完全に説明しません。 使用するための基本的なシナリオ`ThemeDictionary`を指定するには、<xref:System.Windows.ResourceDictionary.Source%2A>のプロパティを`ResourceDictionary`アプリケーション レベルで宣言します。 指定すると、[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]によるアセンブリの`ThemeDictionary`拡張機能ではなく直接[!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)]、拡張機能のロジックがシステム テーマが変更されるたびに適用される無効化ロジックを提供します。  
  
 属性構文は、このマークアップ拡張機能で使用される最も一般的な構文です。 
  `ThemeDictionary` 識別子文字列の後に設定される文字列トークンは、基になる <xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A> 拡張クラスの <xref:System.Windows.ThemeDictionaryExtension> 値として割り当てられます。  
  
 `ThemeDictionary` オブジェクト要素構文にも使用できます。 この場合は、値を指定する、<xref:System.Windows.ThemeDictionaryExtension.AssemblyName%2A>プロパティが必要です。  
  
 `ThemeDictionary` は、<xref:System.Windows.Markup.StaticExtension.Member%2A> プロパティをプロパティおよび値のペアとして指定する詳細出力属性使用でも使用できます。  
  
```xml  
<object property="{ThemeDictionary AssemblyName=assemblyUri}" .../>  
```  
  
 詳細出力の使用は、複数の設定可能プロパティを持つ拡張機能や、一部のプロパティがオプションである場合に役立ちます。 
  `ThemeDictionary` には、必須の設定可能プロパティが 1 つしか存在しないため、このような詳細出力の使用は一般的ではありません。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサの実装でこのマークアップ拡張機能の処理が定義されている、<xref:System.Windows.ThemeDictionaryExtension>クラス。  
  
 `ThemeDictionary` はマークアップ拡張機能です。 一般にマークアップ拡張機能を実装するのは、属性値をリテラル値やハンドラー名以外にエスケープする要件が存在し、その要件の適用範囲がグローバルで、特定の型やプロパティに型コンバーターを適用するだけにとどまらない場合です。 すべてのマークアップ拡張機能で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、{および} される規則は、それぞれの属性構文内の文字を[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサを認識するマークアップ拡張機能が、属性を処理する必要があります。 詳細については、[マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [スタイルとテンプレート](../controls/styling-and-templating.md)
- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [マークアップ拡張機能と WPF XAML](markup-extensions-and-wpf-xaml.md)
- [WPF アプリケーションのリソース ファイル、コンテンツ ファイル、およびデータ ファイル](../app-development/wpf-application-resource-content-and-data-files.md)
