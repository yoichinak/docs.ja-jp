---
title: WPF における分離コードと XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 01122991e99e41259c3b83a38eba002734d749ee
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64655526"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF における分離コードと XAML
<a name="introduction"></a> 分離コード、マークアップ定義のオブジェクトによって結合されるコードの記述に使用される用語は、ときに、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページがマークアップ コンパイルします。 このトピックでは、分離コードの要件および内のコードの別のインライン コード メカニズムについて説明します。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。  
  
 このトピックは、次のセクションで構成されています。  
  
- [必須コンポーネント](#Prerequisites)  
  
- [分離コードと XAML の言語](#codebehind_and_the_xaml_language)  
  
- [分離コード、イベント ハンドラー、および WPF では部分クラスの要件](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x: コード](#x_Code)  
  
- [インライン コードの制限](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、既に読んだことを想定しています、 [XAML の概要 (WPF)](xaml-overview-wpf.md)の基本的な知識があると、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]とオブジェクト指向プログラミングします。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>分離コードと XAML の言語  
 XAML 言語には、マークアップ ファイルの側からのマークアップ ファイルにコード ファイルを関連付けるように言語レベルの機能が含まれています。 具体的には、XAML 言語は、言語機能を定義します。 [X:class ディレクティブ](../../xaml-services/x-class-directive.md)、 [X:subclass ディレクティブ](../../xaml-services/x-subclass-directive.md)、および[X:classmodifier ディレクティブ](../../xaml-services/x-classmodifier-directive.md)します。 コードの生成方法、およびマークアップとコードを統合する方法を正確に XAML 言語の指定の一部ではありません。 コードを統合する方法については、WPF などのフレームワークを一任されて、アプリケーションのプログラミング モデル、およびビルドに XAML を使用するアクションまたは他のサポート方法すべてが必要です。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>分離コード、イベント ハンドラー、および WPF では部分クラスの要件  
  
- 部分クラスは、ルート要素をサポートする型から派生する必要があります。  
  
- マークアップ コンパイルのビルド アクションの既定の動作でしておくことができます、派生部分クラス定義では空白に分離コード側でに注意してください。 コンパイルの結果は指定しない場合でも、ページのルートのバッキング型の部分クラスを基になると見なします。 ただし、この動作に証明書利用者は、ベスト プラクティスではありません。  
  
- 分離コードで記述するイベント ハンドラーは、インスタンス メソッドである必要があり、静的メソッドにすることはできません。 識別される CLR 名前空間内の部分クラスでこれらのメソッドを定義する必要があります`x:Class`します。 指示するイベント ハンドラーの名前を修飾することはできません、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のイベント ハンドラーを別のクラス スコープ内のイベント接続を検索するプロセッサ。  
  
- ハンドラーは、バッキング型システムで適切なイベントのデリゲートに一致する必要があります。  
  
- Microsoft Visual Basic 言語の具体的を使えば、言語固有`Handles`インスタンスとの属性にハンドラーをアタッチする代わりに、ハンドラーの宣言内のイベントにハンドラーを関連付けるキーワード[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 ただし、この手法がいくつかの制限のため、`Handles`キーワードには、すべての特定の機能のサポートできない、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]など特定のイベントのシステム イベントのシナリオのルーティングまたはアタッチされるイベント。 詳細については、次を参照してください。 [Visual Basic と WPF のイベント処理](visual-basic-and-wpf-event-handling.md)します。  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x: コード  
 [X:code](../../xaml-services/x-code-intrinsic-xaml-type.md)ディレクティブ要素で定義されている[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]します。 `x:Code`ディレクティブ要素はインラインのプログラミング コードを含めることができます。 インラインで定義されているコードと対話できます、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]同じページにします。 次の例は、インライン c# コードを示しています。 コードが内部通知、`x:Code`要素と、コードで囲む必要があります`<CDATA[`.`]]>`の内容をエスケープする[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]するように、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]プロセッサ (いずれかの解釈、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]スキーマまたは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スキーマ) 内容を解釈しようとは、文字どおりとして[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]します。  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>インライン コードの制限  
 回避するインライン コードの使用を制限したりすることを検討してください。 アーキテクチャとコーディングの原理の観点からマークアップと分離コードの間の分離の維持は保持デザイナーと開発者の役割もはっきりと区別します。 技術的な詳細レベルでは、インライン コードを記述するコードできます書き込むには、厄介に常に記述するため、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]部分クラスが生成され、既定の XML 名前空間のマッピングのみを使用できます。 追加できないため、`using`ステートメントでは、完全修飾して多くの[!INCLUDE[TLA2#tla_api](../../../../includes/tla2sharptla-api-md.md)]呼び出しを行います。 既定値[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マッピングを含める最もすべてではなく[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]名前空間に存在する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ; 型とその他の CLR 名前空間内に含まれるメンバーの呼び出しを完全に修飾する必要があります。 定義することもできない部分クラスを超えるもので、インライン コードと、メンバーまたは生成された部分クラス内で変数として参照するすべてのユーザー コードのエンティティが存在する必要があります。 その他の言語固有プログラミングの機能、マクロなどまたは`#ifdef`に対してグローバル変数、またはビルド変数を利用することもありません。 詳細については、次を参照してください。 [X:code 組み込み XAML 型](../../xaml-services/x-code-intrinsic-xaml-type.md)します。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [x:Code 組み込み XAML 型 ](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [WPF アプリケーションのビルド](../app-development/building-a-wpf-application-wpf.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
