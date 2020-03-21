---
title: 読み取り専用の依存関係プロパティ
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187181"
---
# <a name="read-only-dependency-properties"></a>読み取り専用の依存関係プロパティ
このトピックでは、既存の読み取り専用の依存関係プロパティ、カスタムの読み取り専用の依存関係プロパティを作成するシナリオと手法など、読み取り専用の依存関係プロパティについて説明します。  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、依存関係プロパティの実装の基本シナリオとカスタム依存関係プロパティへのメタデータの適用方法を理解していることを前提とします。 詳細については、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」および「[依存関係プロパティのメタデータ](dependency-property-metadata.md)」を参照してください。  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>既存の読み取り専用の依存関係プロパティ  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] フレームワークで定義されている依存関係プロパティの一部は読み取り専用です。 読み取り専用の依存関係プロパティを指定する一般的な理由は、それらが状態決定に使用されるプロパティであるにも関わらず、その状態は多くの要因の影響を受け、プロパティをその状態に設定するだけではユーザー インターフェイス設計の観点から望ましくないことにあります。 たとえば、プロパティ<xref:System.Windows.UIElement.IsMouseOver%2A>は実際にはマウス入力から決定された状態を表示するだけです。 実際にマウス入力を行わずにプログラムでこの値を設定しようとすると、予期しない結果になり、不整合が生じる原因になります。  
  
 設定可能ではないため、読み取り専用の依存関係プロパティは、依存関係プロパティがソリューションを通常提供するシナリオの多くには適切ではありません (データ バインディング、直接スタイル設定可能な値、検証、アニメーション、継承など)。 それでも、設定不可能な読み取り専用依存関係プロパティには、プロパティ システムの依存関係プロパティによってサポートされるいくつかの追加機能があります。 その他の機能のうち最も重要なのは、読み取り専用の依存関係プロパティはスタイルのプロパティ トリガーとして使用できることです。 通常の共通言語ランタイム (CLR) プロパティでは、トリガーを有効にすることはできません。依存関係プロパティである必要があります。 前述<xref:System.Windows.UIElement.IsMouseOver%2A>のプロパティは、コントロールのスタイルを定義すると非常に便利なシナリオの例であり、コントロール内の複合要素の背景、前景、または類似のプロパティなどの表示可能なプロパティは、ユーザーがコントロールの定義済みの領域にマウスを置くと変化します。 読み取り専用の依存関係プロパティの変化は、プロパティ システム固有の無効化プロセスによって検出して報告することもでき、これは実際にはプロパティ トリガー機能を内部的にサポートします。  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>読み取り専用のカスタム依存関係プロパティの作成  
 多くの一般的な依存関係プロパティのシナリオで読み取り専用依存関係プロパティが機能しない理由に関する前のセクションを参照してください。 ただし、適切なシナリオがある場合は、独自の読み取り専用依存関係プロパティを作成してもかまいません。  
  
 読み取り専用の依存関係プロパティを作成するプロセスの大部分は、「[カスタム依存関係プロパティ](custom-dependency-properties.md)」と「[依存関係プロパティの実装](how-to-implement-a-dependency-property.md)」のトピックの説明と同じです。 ただし、次の 3 つの重要な違いがあります。  
  
- プロパティを登録する場合は、<xref:System.Windows.DependencyProperty.RegisterReadOnly%2A>プロパティ登録の通常<xref:System.Windows.DependencyProperty.Register%2A>のメソッドではなく、メソッドを呼び出します。  
  
- CLR の "ラッパー" プロパティを実装する場合は、公開するパブリック ラッパーの読み取り専用状態に不整合が生じないように、ラッパーにもセット実装がないことを確認します。  
  
- 読み取り専用登録によって返されるオブジェクト<xref:System.Windows.DependencyPropertyKey>は、<xref:System.Windows.DependencyProperty>ではなく です。 やはりこのフィールドをメンバーとして格納する必要がありますが、通常は、型のパブリック メンバーにはしません。  
  
 読み取り専用の依存関係プロパティを補足するために使用するプライベートのフィールドまたは値はすべて、適当なロジックを使用して完全に書き込み可能にしてかまいません。 ただし、プロパティを最初に設定する方法、またはランタイム ロジックの一部として設定する最も簡単な方法は、プロパティ システムを回避してプライベート バッキング フィールドを直接設定するのではなく、プロパティ システムの API を使用することです。 特に、型<xref:System.Windows.DependencyObject.SetValue%2A><xref:System.Windows.DependencyPropertyKey>のパラメータを受け入れる シグネチャがあります。 アプリケーション ロジック内でこの値をプログラムで設定する方法と場所は、依存関係プロパティを最初に登録したときに<xref:System.Windows.DependencyPropertyKey>作成されたに対するアクセスの設定方法に影響します。 このロジックすべてをクラス内で処理する場合はプライベートにでき、アセンブリの他の部分から設定する必要がある場合は内部に設定します。 1 つの方法は<xref:System.Windows.DependencyObject.SetValue%2A>、格納されたプロパティ値を変更する必要があることをクラス インスタンスに通知する関連イベントのクラス イベント ハンドラー内で呼び出す方法です。 もう 1 つの方法は、登録時にこれらの<xref:System.Windows.PropertyChangedCallback>プロパティ<xref:System.Windows.CoerceValueCallback>のメタデータの一部として、ペアとコールバックを使用して依存関係プロパティを結び付ける方法です。  
  
 <xref:System.Windows.DependencyPropertyKey>はプライベートであり、プロパティ システムによってコードの外部に伝達されないため、読み取り専用の依存関係プロパティは、読み取り/書き込み依存関係プロパティよりも設定の方が優れています。 読み取り/書き込み依存関係プロパティの場合は、識別するフィールドは明示的または暗黙的にパブリックであり、したがってプロパティは広範に設定可能です。 詳細については、「[依存関係プロパティのセキュリティ](dependency-property-security.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [依存関係プロパティの概要](dependency-properties-overview.md)
- [カスタム依存関係プロパティ](custom-dependency-properties.md)
- [スタイルとテンプレート](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
