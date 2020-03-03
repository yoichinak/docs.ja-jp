---
title: LINQ to XML データバインディングの例
ms.date: 10/22/2019
ms.topic: sample
helpviewer_keywords:
- linq to xml data binding sample
ms.openlocfilehash: aac814e4768a863a93e69e34cd18c941a9b35c89
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2019
ms.locfileid: "72921222"
---
# <a name="linq-to-xml-data-binding-sample"></a>LINQ to XML データバインディングのサンプル

この記事では、ユーザーインターフェイスコンポーネントを埋め込み XML データソースにバインドする Windows Presentation Foundation (WPF) アプリである LinqToXmlDataBinding サンプルについて説明します。

## <a name="overview"></a>概要

LinqToXmlDataBinding サンプルは、および XAML ソースファイルを含むC# WINDOWS PRESENTATION FOUNDATION (WPF) アプリです。 埋め込み XML ドキュメントには、書籍の一覧が定義されています。 ユーザーは、アプリを使用して、ブックのエントリを表示、追加、削除、および編集できます。

プライマリソースファイルは2つあります。

- [L2DBForm.xaml](l2dbform-xaml-source-code.md) には、メイン ウィンドウのユーザー インターフェイス (UI) の XAML 宣言コードが含まれています。 また、データプロバイダーと、書籍の一覧の埋め込み XML ドキュメントを定義するウィンドウリソースセクションも含まれています。

- [L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md) には、UI に関連付けられている初期化メソッドとイベント処理メソッドが含まれています。

メイン ウィンドウは縦に区切られ、次の 4 つの UI セクションに分かれています。

- **[XML]** には、組み込まれている書籍一覧の生の XML ソースが表示されます。

- **[Book List]** には書籍エントリが標準テキストで表示され、ユーザーはエントリを個別に選択および削除できます。

- **[Edit Selected Book]** では、ユーザーは現在選択している書籍エントリに関連付けられている値を編集できます。

- **[Add New Book]** では、ユーザーが入力した値に基づいて新しい書籍エントリを作成できます。

## <a name="run-the-sample"></a>サンプルを実行する

このセクションでは、Visual Studio で LinqToXmlDataBinding プロジェクトを作成してビルドする方法と、結果の LinqToXmlDataBinding Windows Presentation Foundation (WPF) アプリを実行する方法について説明します。

### <a name="create-the-project"></a>プロジェクトの作成

1. Visual Studio を開き、**LinqToXmlDataBinding** という名前の C# **WPF アプリ**を作成します。

   プロジェクトの対象は、.NET Framework 3.5 (またはそれ以降) にする必要があります。

1. 次の .NET アセンブリ用のプロジェクト参照がない場合は追加します。

    - System.Data
    - System.Data.DataSetExtensions
    - System.Xml
    - System.Xml

1. **Ctrl** キーと **Shift** キーを押しながら **B** キーを押してソリューションをビルドし、**F5** キーを押してそのソリューションを実行します。

   プロジェクトがエラーなくコンパイルされ、汎用 WPF アプリケーションとして実行されます。

### <a name="add-code"></a>コードの追加

1. **ソリューション エクスプローラー**でソース ファイルの名前を **Window1.xaml** から **L2XDBForm.xaml** に変更します。

   依存ソースファイル Window1.xaml.cs の名前は自動的に L2XDBForm.xaml.cs に変更されます。

1. **L2xdbform.xaml**ファイルで見つかったソースコードを[l2dbform.xaml ソースコード](l2dbform-xaml-source-code.md)に置き換えます。 このファイルは XAML ソース ビューで操作します。

1. 同様に、 **L2XDBForm.xaml.cs**内のソースを[L2DBForm.xaml.cs ソースコード](l2dbform-xaml-cs-source-code.md)に置き換えます。

1. **ファイル app.xaml で、文字列** **window1.xaml**のすべての出現箇所を**l2xdbform.xaml**に置き換えます。

1. **Ctrl** キーと **Shift** キーを押しながら **B** キーを押して、ソリューションをビルドします。

### <a name="run-the-app"></a>アプリを実行する

LinqToXmlDataBinding アプリを使用すると、埋め込み XML 要素として格納されている書籍の一覧を表示および操作できます。 **F5**キー ([デバッグ開始]) または**Ctrl**+**F5** ([デバッグなしで開始]) を押して、アプリを実行します。

**[WPF Data Binding using LINQ to XML]** というタイトルのプログラム ウィンドウが表示されます。

UI の上部のセクションには、書籍リストを表す未加工の**XML**が表示されます。 この部分は WPF の <xref:System.Windows.Controls.TextBlock> コントロールを使って表示されており、マウスやキーボードで操作できません。

**[Book List]** というラベルの付いた 2 番目のセクションには、プレーンテキストの順序付けられた一覧として書籍が表示されます。 この部分では <xref:System.Windows.Controls.ListBox> コントロールが使用されており、マウスまたはキーボードによる選択が可能です。

### <a name="add-and-delete-books"></a>ブックの追加と削除

一覧に新しい書籍を追加するには、 **[新しい書籍の追加]** の **[ID]** と **[値]** <xref:System.Windows.Controls.TextBox> コントロールに値を入力し、add **[book]** を選択します。 書籍と XML の両方の一覧に書籍が追加されます。 このプログラムでは入力値が検証されません。

一覧から既存の書籍を削除するには、 **[Book list]** セクションでそのブックを選択し、 **[選択したブックの削除]** を選択します。 書籍のエントリは、書籍と未加工の XML ソースの一覧の両方から削除されます。

### <a name="edit-a-book-entry"></a>書籍のエントリを編集する

1. 2 番目の **[Book List]** セクションで書籍エントリを選択します。

   現在の値は、 **[選択したブックの編集]** セクションに表示されます。

1. キーボードを使用して値を編集します。 <xref:System.Windows.Controls.TextBox> 制御がフォーカスを失うとすぐに、変更は XML ソースと書籍の一覧に自動的に反映されます。
