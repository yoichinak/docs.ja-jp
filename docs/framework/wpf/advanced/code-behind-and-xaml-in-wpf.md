---
title: WPF における分離コードと XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], code-behind
- code-behind files [WPF], XAML
ms.assetid: 9df6d3c9-aed3-471c-af36-6859b19d999f
ms.openlocfilehash: acd8c9ff0a4ff718dba272958a3e63820bcf1354
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401612"
---
# <a name="code-behind-and-xaml-in-wpf"></a>WPF における分離コードと XAML
<a name="introduction"></a>分離コードとは、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ページがマークアップコンパイルされたときに、マークアップ定義オブジェクトと結合されるコードを記述するために使用される用語です。 このトピックでは、分離コードの要件、およびの[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]コードの代替インラインコード機構について説明します。  
  
 このトピックは、次のセクションで構成されています。  
  
- [必須コンポーネント](#Prerequisites)  
  
- [分離コードと XAML 言語](#codebehind_and_the_xaml_language)  
  
- [WPF の分離コード、イベントハンドラー、および部分クラスの要件](#Code_behind__Event_Handler__and_Partial_Class)  
  
- [x:Code](#x_Code)  
  
- [インラインコードの制限事項](#Inline_Code_Limitations)  
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、「XAML の[概要 (WPF)」](xaml-overview-wpf.md)を読み、CLR とオブジェクト指向プログラミングに関する基本的な知識を持っていることを前提としています。  
  
<a name="codebehind_and_the_xaml_language"></a>   
## <a name="code-behind-and-the-xaml-language"></a>分離コードと XAML 言語  
 XAML 言語には、マークアップファイル側からコードファイルをマークアップファイルに関連付けることができるようにする言語レベルの機能が含まれています。 具体的には、XAML 言語では、言語機能の[X:Class ディレクティブ](../../xaml-services/x-class-directive.md)、 [x:Subclass ディレクティブ](../../xaml-services/x-subclass-directive.md)、および[x:ClassModifier ディレクティブ](../../xaml-services/x-classmodifier-directive.md)が定義されています。 コードをどのように生成するか、およびマークアップとコードを統合する方法は、XAML 言語が指定する内容の一部ではありません。 WPF などのフレームワークによって、コードを統合する方法、アプリケーションとプログラミングモデルで XAML を使用する方法、ビルドアクションやその他のすべてのサポートが必要であるかどうかが決定されます。  
  
<a name="Code_behind__Event_Handler__and_Partial_Class"></a>   
## <a name="code-behind-event-handler-and-partial-class-requirements-in-wpf"></a>WPF の分離コード、イベントハンドラー、および部分クラスの要件  
  
- 部分クラスは、ルート要素をバッキングする型から派生する必要があります。  
  
- マークアップコンパイルビルドアクションの既定の動作では、分離コード側の部分クラス定義で派生を空白のままにすることができます。 コンパイルされた結果は、指定されていない場合でも、ページルートのバッキング型が部分クラスの基礎となることを前提としています。 ただし、この動作に依存することは、ベストプラクティスではありません。  
  
- 分離コードで記述するイベントハンドラーは、インスタンスメソッドである必要があり、静的メソッドにすることはできません。 これらのメソッドは、で`x:Class`識別される CLR 名前空間内の部分クラスで定義する必要があります。 イベントハンドラーの名前を修飾して、異なるクラススコープ[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]内のイベントのイベントハンドラーを検索するようにプロセッサに指示することはできません。  
  
- ハンドラーは、バッキング型システム内の適切なイベントのデリゲートと一致する必要があります。  
  
- 特に Microsoft Visual Basic 言語では、の`Handles` [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]属性を持つハンドラーをアタッチするのではなく、言語固有のキーワードを使用してハンドラーをハンドラー宣言内のインスタンスおよびイベントに関連付けることができます。 ただし、この方法にはいくつかの制限`Handles`があります。これは、特定のルーティング[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベントシナリオや添付イベントなど、イベントシステムの特定の機能をすべてサポートすることができないためです。 詳細については、「 [Visual Basic と WPF のイベント処理](visual-basic-and-wpf-event-handling.md)」を参照してください。  
  
<a name="x_Code"></a>   
## <a name="xcode"></a>x:Code  
 [x:Code](../../xaml-services/x-code-intrinsic-xaml-type.md)は、で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]定義されたディレクティブ要素です。 ディレクティブ`x:Code`要素には、インラインプログラミングコードを含めることができます。 インラインで定義されているコードは、 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]同じページでと対話できます。 次の例は、 C#インラインコードを示しています。 コードが`x:Code`要素内にあり、コードを囲む必要があることに注意`<CDATA[`してください。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]の内容をエスケープして、(スキーマまたはスキーマのいずれかを解釈する) プロセッサが内容を文字どおりに解釈しようとしないようにします。 [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] `]]>`  
  
 [!code-xaml[XAMLOvwSupport#ButtonWithInlineCode](~/samples/snippets/csharp/VS_Snippets_Wpf/XAMLOvwSupport/CSharp/page4.xaml#buttonwithinlinecode)]  
  
<a name="Inline_Code_Limitations"></a>   
## <a name="inline-code-limitations"></a>インラインコードの制限事項  
 インラインコードの使用を回避または制限することを検討してください。 アーキテクチャとコーディングの理念に関して、マークアップと分離コードの分離を維持することで、デザイナーと開発者のロールがより明確になります。 より技術的なレベルでは、インラインコード用に記述するコードは、常に[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]生成された部分クラスに書き込みを行い、既定の XML 名前空間マッピングのみを使用できるため、記述しにくい場合があります。 ステートメントを追加`using`することはできないため、作成する API 呼び出しの多くを完全に修飾する必要があります。 既定[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のマッピングには、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アセンブリに存在するほとんどの CLR 名前空間が含まれますが、他の clr 名前空間内に含まれる型およびメンバーの呼び出しを完全に修飾する必要があります。 また、インラインコードで部分クラスを超えるものを定義することはできません。また、参照するすべてのユーザーコードエンティティは、生成された部分クラス内のメンバーまたは変数として存在する必要があります。 マクロや`#ifdef` 、グローバル変数やビルド変数など、言語固有のプログラミング機能も使用できません。 詳細については、「 [X:Code 組み込み XAML 型](../../xaml-services/x-code-intrinsic-xaml-type.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XAML の概要 (WPF)](xaml-overview-wpf.md)
- [x:Code 組み込み XAML 型 ](../../xaml-services/x-code-intrinsic-xaml-type.md)
- [WPF アプリケーションのビルド](../app-development/building-a-wpf-application-wpf.md)
- [XAML 構文の詳細](xaml-syntax-in-detail.md)
