---
title: 分離コードと XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: 32283d5b81bf92999a97711ded13a8b533ae3028
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145346"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF における分離コードと XAML
<a name="introduction"></a>分離コードは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]マークアップ定義オブジェクトと結合されるコードを記述するために使用される用語で、ページがマークアップ コンパイルされます。 このトピックでは、コードビハインドの要件と、 の[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードの代替インライン コードメカニズムについて説明します。  
  
 このトピックには、次のセクションが含まれます。  
  
- [前提条件](#Prerequisites)  
  
- [分離コードと XAML 言語](#codebehind_and_the_xaml_language)  
  
- [WPF の分離コード、イベント ハンドラー、および部分クラスの要件](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:コード](#x_Code)  
  
- [インライン コードの制限事項](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは[、XAML の概要 (WPF) を](../../../desktop-wpf/fundamentals/xaml.md)読み、CLR とオブジェクト指向プログラミングの基本的な知識を持っていることを前提としています。  
  
<a name="codebehind_and_the_xaml_language"></a>
## <a name="code-behind-and-the-xaml-language"></a>分離コードと XAML 言語  
 XAML 言語には、マークアップ ファイル側からコード ファイルをマークアップ ファイルに関連付けるための言語レベルの機能が含まれています。 具体的には、XAML 言語は、言語機能[x: クラス ディレクティブ](../../../desktop-wpf/xaml-services/xclass-directive.md) [、x:サブクラス ディレクティブ](../../../desktop-wpf/xaml-services/xsubclass-directive.md)、および[x:ClassModifier ディレクティブ](../../../desktop-wpf/xaml-services/xclassmodifier-directive.md)を定義します。 コードの生成方法とマークアップとコードの統合方法は、XAML 言語が指定する部分ではありません。 コードの統合方法、アプリケーション モデルとプログラミング モデルで XAML を使用する方法、およびこのすべてに必要なビルド アクションやその他のサポートを決定するのは、WPF などのフレームワークに任されています。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF の分離コード、イベント ハンドラー、および部分クラスの要件  
  
- 部分クラスは、ルート要素をバックする型から派生する必要があります。  
  
- マークアップ コンパイル ビルド アクションの既定の動作では、分離コード側の部分クラス定義で派生を空白のままにできます。 コンパイルされた結果は、ページ ルートのバッキング型が、指定されていない場合でも部分クラスの基礎であると想定します。 ただし、この動作に依存することはベスト プラクティスではありません。  
  
- 分離コードで記述するイベント ハンドラーは、インスタンス メソッドである必要があり、静的メソッドで指定することはできません。 これらのメソッドは、 で識別される CLR 名前空間内の部分`x:Class`クラスで定義する必要があります。 イベント ハンドラの名前を修飾して、プロセッサに対[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]して、別のクラス スコープでのイベント ワイヤリングのイベント ハンドラを探す指示を行うことはできません。  
  
- ハンドラーは、バッキング型システムの適切なイベントのデリゲートと一致する必要があります。  
  
- 特に Microsoft Visual Basic 言語では、言語固有`Handles`のキーワードを使用して、ハンドラーをハンドラー宣言のインスタンスおよびイベントに[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]関連付けることができます。 ただし、この方法では、`Handles`特定のルーティング イベント シナリオや添付イベントなど、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント システムの特定の機能をすべてサポートできないという制限があります。 詳細については、「 [Visual Basic および WPF イベント処理](visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
<a name="x_Code"></a>
## <a name="xcode"></a>x:コード  
 [x:コード](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)は で定義されたディレクティブ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]要素です。 ディレクティブ`x:Code`要素には、インライン プログラミング コードを含めることができます。 インラインで定義されたコードは、同じページ上[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]で 対話できます。 インライン C# コードの例を次に示します。 コードが要素の`x:Code`内部にあり、コードを . `<CDATA[`を使用して XML の内容をエスケープ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]し、プロセッサ (スキーマまたは[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スキーマを解釈する) が、その内容を XML として文字通り解釈しようとしない場合。 `]]>` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>
## <a name="inline-code-limitations"></a>インライン コードの制限事項  
 インライン コードの使用を避けるか制限することを検討してください。 アーキテクチャとコーディングの哲学の観点から、マークアップと分離コードの分離を維持することで、デザイナーと開発者の役割が明確になります。 技術的なレベルでは、インライン コード用に記述するコードは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]生成された部分クラスに常に書き込み中であり、既定の XML 名前空間マッピングのみを使用できるため、記述が厄介になる可能性があります。 ステートメントを追加`using`することはできないため、実行する API 呼び出しの多くを完全に修飾する必要があります。 既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のマッピングには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリ内に存在する CLR 名前空間の大部分が含まれますが、すべての CLR 名前空間が含まれるわけではありません。他の CLR 名前空間に含まれる型とメンバーの呼び出しを完全に修飾する必要があります。 また、インライン コードで部分クラス以外の要素を定義することもできず、参照するすべてのユーザー コード エンティティは、生成された部分クラス内にメンバーまたは変数として存在する必要があります。 マクロやグローバル変数や`#ifdef`ビルド変数に対する言語固有のプログラミング機能も利用できません。 詳細については、「 [x: コード組み込み XAML 型](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](../../../desktop-wpf/fundamentals/xaml.md)
- [x:Code 組み込み XAML 型 ](../../../desktop-wpf/xaml-services/xcode-intrinsic-xaml-type.md)
- [WPF アプリケーションのビルド](../app-development/building-a-wpf-application-wpf.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
