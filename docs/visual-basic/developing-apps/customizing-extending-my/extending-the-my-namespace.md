---
title: Visual Basic における My 名前空間の拡張
ms.date: 07/20/2015
f1_keywords:
- vb.AddingMyExtensions
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: 808e8617-b01c-4135-8b21-babe87389e8e
ms.openlocfilehash: 4d7bb6eef398746a4bd2dc4dbf3d526da1c1e0f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62014220"
---
# <a name="extending-the-my-namespace-in-visual-basic"></a>Visual Basic における My 名前空間の拡張
`My`プロパティとメソッドを .NET Framework の能力を簡単に利用できるようにする Visual Basic における名前空間を公開します。 `My`名前空間には一般的なプログラミングの問題を 1 行のコードに多くの場合、困難な作業を減らすことが簡略化します。 さらに、`My`の動作をカスタマイズできるように、名前空間が完全に拡張可能`My`特定のアプリケーションのニーズに対応するには、その階層に新しいサービスを追加します。 このトピックでは両方の既存のメンバーをカスタマイズする方法、`My`名前空間と、独自のカスタム クラスを追加する方法、`My`名前空間。  
  
 **トピックのコンテンツ**  
  
- [既存の Namespace メンバーは自分のカスタマイズ](#customizing)  
  
- [オブジェクトにメンバーを追加します。](#addingtoobjects)  
  
- [カスタム オブジェクトを追加、My Namespace](#addingcustom)  
  
- [メンバーを追加、My Namespace](#addingtonamespace)  
  
- [カスタム My オブジェクトへのイベントの追加](#addingevents)  
  
- [デザイン ガイドライン](#design)  
  
- [用のクラス ライブラリのデザイン、](#designing)  
  
- [パッケージ化と拡張機能の配置](#packaging)  
  
## <a name="customizing"></a> 既存の Namespace メンバーは自分のカスタマイズ  
 `My` Visual Basic の公開で名前空間は、アプリケーションや、コンピューターに関する情報を頻繁に使用します。 内のオブジェクトの完全な一覧については、`My`名前空間を参照してください[My の参照を](../../../visual-basic/language-reference/keywords/my-reference.md)します。 既存のメンバーをカスタマイズする必要があります、`My`名前空間にするようは、アプリケーションのニーズを満たします。 内のオブジェクトの任意のプロパティ、`My`読み取り専用でない名前空間は、カスタム値に設定することができます。  
  
 たとえば、頻繁に使用する、`My.User`アプリケーションを実行しているユーザーの現在のセキュリティ コンテキストにアクセスするオブジェクト。 ただし、会社がカスタムのユーザー オブジェクトを使用して、追加情報と、会社内のユーザーの機能を公開します。 このシナリオでの既定値を置き換えることができます、`My.User.CurrentPrincipal`プロパティに次の例で示すように、独自カスタム プリンシパル オブジェクトのインスタンスを使用します。  
  
 [!code-vb[VbVbcnExtendingMy#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#1)]  
  
 設定、`CurrentPrincipal`プロパティを`My.User`オブジェクトが、アプリケーションを実行する id を変更します。 `My.User`オブジェクトは、さらに、新しく指定したユーザーに関する情報を返します。  
  
## <a name="addingtoobjects"></a> オブジェクトにメンバーを追加します。  
 返される型`My.Application`と`My.Computer`として定義されます`Partial`クラス。 そのため、拡張することができます、`My.Application`と`My.Computer`オブジェクトを作成して、`Partial`という名前のクラス`MyApplication`または`MyComputer`します。 クラスにすることはできません、`Private`クラス。 一部として、クラスを指定する場合、`My`名前空間には、プロパティとに含まれるメソッドを追加できる、`My.Application`または`My.Computer`オブジェクト。  
  
 たとえば、次の例はという名前のプロパティを追加します。`DnsServerIPAddresses`を、`My.Computer`オブジェクト。  
  
 [!code-vb[VbVbcnExtendingMy#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class2.vb#2)]  
  
## <a name="addingcustom"></a> カスタム オブジェクトを追加、My Namespace  
 ですが、`My`名前空間では、多くの一般的なプログラミング タスクのソリューション、タスクが発生する可能性があります`My`名前空間が対応していません。 たとえば、アプリケーションが、ユーザー データのカスタム ディレクトリ サービスにアクセスまたはアプリケーションは、Visual Basic では既定でインストールされていないアセンブリを使用可能性があります。 拡張することができます、`My`環境に固有の一般的なタスクへのカスタム ソリューションを含める名前空間。 `My`名前空間は、増え続けるアプリケーションのニーズを満たすために新しいメンバーを追加する簡単に拡張できます。 さらに、展開、`My`名前空間の拡張機能を Visual Basic テンプレートとして他の開発者。  
  
### <a name="addingtonamespace"></a> メンバーを追加、My Namespace  
 `My`名前空間には、他の名前空間のようなプロパティを追加できます最上位レベルにモジュールを追加して、指定するだけで、`Namespace`の`My`します。 使用して、モジュールの注釈を付け、`HideModuleName`属性の次の例に示すようにします。 `HideModuleName`属性により、IntelliSense が表示されないよう、モジュール名のメンバーを表示するとき、`My`名前空間。  
  
 [!code-vb[VbVbcnExtendingMy#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#3)]  
  
 メンバーを追加する、`My`名前空間、モジュールに必要なプロパティを追加します。 追加の各プロパティの`My`名前空間、型のプライベート フィールドを追加する`ThreadSafeObjectProvider(Of T)`型は、カスタム プロパティによって返される型です。 このフィールドは呼び出すことによって、プロパティによって返されるスレッド セーフなオブジェクト インスタンスの作成に使用、`GetInstance`メソッド。 その結果、拡張プロパティにアクセスする各スレッドは、戻り値の型のインスタンスを受け取ります。 次の例は、という名前のプロパティを追加します。`SampleExtension`型のある`SampleExtension`を、`My`名前空間。  
  
 [!code-vb[VbVbcnExtendingMy#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#4)]  
  
## <a name="addingevents"></a> カスタム My オブジェクトへのイベントの追加  
 使用することができます、`My.Application`オブジェクトのカスタム イベントを公開する`My`オブジェクトを拡張することによって、`MyApplication`部分クラスに、`My`名前空間。 Windows ベースのプロジェクトでは、ダブルクリックすることができます、 **My Project**にプロジェクトのノード**ソリューション エクスプ ローラー**します。 Visual Basic で**プロジェクト デザイナー**、クリックして、 `Application`  タブをクリックして、`View Application Events`ボタンをクリックします。 ApplicationEvents.vb という新しいファイルが作成されます。 拡張するための次のコードが含まれている、`MyApplication`クラス。  
  
 [!code-vb[VbVbcnExtendingMy#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#5)]  
  
 イベント ハンドラーを追加するには、カスタム`My`オブジェクトにカスタム イベント ハンドラーを追加することで、`MyApplication`クラス。 カスタム イベントでは、イベント ハンドラーを追加すると、削除、またはイベントが発生したときに実行されるコードを追加することができます。 なお、`AddHandler`コードのカスタム イベントがイベントを処理するユーザー コードを追加した場合にのみを実行します。 などを検討してください、`SampleExtension`オブジェクト、前のセクションからには、`Load`のカスタム イベント ハンドラーを追加するイベントです。 次のコード例は、という名前のカスタム イベント ハンドラーを示しています。`SampleExtensionLoad`はされると呼び出されます、`My.SampleExtension.Load`イベントが発生します。 新しいを処理するコードを追加するときに`My.SampleExtensionLoad`、イベント、`AddHandler`このカスタム イベント コードの一部を実行します。 `MyApplication_SampleExtensionLoad`メソッドが処理するイベント ハンドラーの例を示すコード例に含まれる、`My.SampleExtensionLoad`イベント。 なお、`SampleExtensionLoad`を選択すると、イベントが表示されます、**マイ アプリケーション イベント**左側のドロップダウン リストの上、コード エディター、ApplicationEvents.vb ファイルを編集するときのオプション。  
  
 [!code-vb[VbVbcnExtendingMy#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnExtendingMy/VB/Class1.vb#6)]  
  
## <a name="design"></a> デザイン ガイドライン  
 拡張機能を開発する際に、`My`名前空間の拡張機能コンポーネントのメンテナンス コストを最小限に抑えるため、次のガイドラインを使用します。  
  
- **拡張機能のロジックのみが含まれます。** 含まれるロジック、`My`名前空間の拡張機能に必要な機能を公開するために必要なコードのみを含める必要があります、`My`名前空間。 拡張機能は、ソース コードとしてユーザーのプロジェクトに存在するため拡張コンポーネントを更新高メンテナンス費用が発生し、可能であれば避ける必要があります。  
  
- **プロジェクトの前提条件を最小限に抑えます。** 拡張機能を作成するとき、`My`名前空間には、一連の参照、プロジェクト レベルのインポート、または特定のコンパイラ設定と見なさないでください (たとえば、`Option Strict`オフ)。 代わりに、依存関係を最小限に抑えるし、を使用してすべての型参照を完全に修飾、`Global`キーワード。 また、使用、拡張機能をコンパイルすることを確認`Option Strict`の拡張機能でエラーを最小限に抑える。  
  
- **拡張機能のコードを分離します。** 1 つのファイル、コードを配置すると、拡張機能が Visual Studio 項目テンプレートとして簡単にデプロイ可能にします。 詳細については、このトピックの「「パッケージ化と拡張機能の配置」を参照してください。 すべてを配置すること、`My`名前空間の拡張機能コードを 1 つのファイルまたはプロジェクト内の別のフォルダーはユーザーの検索をヘルプも、`My`名前空間の拡張機能。  
  
## <a name="designing"></a> 用のクラス ライブラリのデザイン、  
 ほとんどのオブジェクト モデルを使用した場合と同様に、いくつかの設計パターンが正常に動作、`My`名前空間とその他のユーザーはありません。 拡張機能を設計するときに、`My`名前空間には、次の原則を検討してください。  
  
- **ステートレスな方法があります。** 内のメソッド、`My`名前空間は、特定のタスクに完全なソリューションを提供する必要があります。 メソッドに渡されるパラメーター値が特定のタスクを完了するために必要なすべての入力を提供することを確認します。 リソースへの開いている接続など、前の状態に依存するメソッドを作成しないでください。  
  
- **グローバル インスタンス。** 管理されている唯一の状態、`My`名前空間は、プロジェクトに対してグローバルです。 たとえば、`My.Application.Info`アプリケーション全体で共有されている状態をカプセル化します。  
  
- **単純なパラメーターの型。** 複雑なパラメーターの型を回避することで、単純なモ ノを保持します。 代わりに、入力パラメーターを受け取らないメソッドを作成または文字列プリミティブ型、やなどの簡単な入力型を受け取る。  
  
- **ファクトリ メソッド。** 一部の型がインスタンス化することが困難です。 ファクトリ メソッドを提供する拡張機能として、`My`名前空間より簡単に検出し、このカテゴリに分類される型を使用することができます。 適切に動作するファクトリ メソッドの例は、`My.Computer.FileSystem.OpenTextFileReader`します。 いくつかのストリーム型は .NET Framework で使用できます。 具体的には、テキスト ファイルを指定することによって、`OpenTextFileReader`をユーザーが使用するストリームの理解に役立ちます。  
  
 次のガイドラインは、クラス ライブラリの一般的な設計原則を妨害しません。 代わりに、Visual Basic を使用している開発者向けに最適化されている推奨事項は、`My`名前空間。 クラス ライブラリを作成するための一般的な設計原則を参照してください。 [Framework デザイン ガイドライン](../../../standard/design-guidelines/index.md)します。  
  
## <a name="packaging"></a> パッケージ化と拡張機能の配置  
 含めることができます`My`、Visual Studio プロジェクト テンプレートの名前空間の拡張機能は、拡張機能をパッケージ化し、それを Visual Studio 項目テンプレートとしてデプロイします。 パッケージ化するときに、`My`として、Visual Studio 項目テンプレートの名前空間の拡張機能、Visual Basic で提供される追加機能を活用を実行できます。 これらの機能をプロジェクトは、特定のアセンブリを参照するときに、拡張機能を含めることを有効にまたは明示的に追加するユーザーを有効にする、`My`名前空間の拡張機能を使用して、**マイ拡張**Visual Basic のページプロジェクト デザイナー。  
  
 デプロイする方法の詳細について`My`名前空間の拡張機能を参照してください[パッケージ化と展開のカスタム マイ拡張](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)します。  
  
## <a name="see-also"></a>関連項目

- [カスタム My 拡張のパッケージ化と配置](../../../visual-basic/developing-apps/customizing-extending-my/packaging-and-deploying-custom-my-extensions.md)
- [Visual Basic アプリケーション モデルの拡張](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)
- [My で利用可能なオブジェクトのカスタマイズ](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
- [[マイ拡張] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)
- [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)
- [Partial](../../../visual-basic/language-reference/modifiers/partial.md)
