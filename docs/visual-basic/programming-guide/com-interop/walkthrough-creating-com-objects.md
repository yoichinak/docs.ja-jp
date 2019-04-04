---
title: 'チュートリアル: Visual Basic で COM オブジェクトの作成'
ms.date: 07/20/2015
helpviewer_keywords:
- COM interop [Visual Basic], creating COM objects
- COM objects, creating
- COM interop [Visual Basic], walkthroughs
- object creation [Visual Basic], COM objects
- COM objects, walkthroughs
ms.assetid: 7b07a463-bc72-4392-9ba0-9dfcb697a44f
ms.openlocfilehash: 5fc0105cffb5606f9382aca7b55d6544d04f9fe7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838158"
---
# <a name="walkthrough-creating-com-objects-with-visual-basic"></a>チュートリアル: Visual Basic で COM オブジェクトの作成
新しいアプリケーションまたはコンポーネントを作成する場合は、.NET Framework アセンブリを作成することをお勧めします。 ただし、Visual Basic も簡単に .NET Framework コンポーネントを COM に公開 これにより、COM コンポーネントを必要とする以前のアプリケーション スイートの新しいコンポーネントを提供することができます。 Visual Basic を使用して公開する方法についても説明[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]COM クラス テンプレートの有無にかかわらず、COM オブジェクトとしてのオブジェクト。  
  
 COM クラス テンプレートを使用する COM オブジェクトを公開する最も簡単な方法です。 COM クラス テンプレートは、新しいクラスを作成し、COM オブジェクトとしてクラスおよび相互運用性レイヤーを生成し、オペレーティング システムに登録するプロジェクトを構成します。  
  
> [!NOTE]
>  Visual Basic で使用するアンマネージ コードの COM オブジェクトとして作成したクラスを公開することも、本当の COM オブジェクトでないし、Visual Basic では使用できません。 詳細については、[.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)を参照してください。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-com-object-by-using-the-com-class-template"></a>COM クラス テンプレートを使用して COM オブジェクトを作成するには  
  
1.  新しい Windows アプリケーション プロジェクトを開き、**ファイル**メニューをクリックして**新しいプロジェクト**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックス、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。 選択**クラス ライブラリ**から、**テンプレート**ボックスの一覧をクリックして**OK**します。 新しいプロジェクトが表示されます。  
  
3.  選択**新しい項目の追加**から、**プロジェクト**メニュー。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
4.  選択**COM クラス**から、**テンプレート**ボックスの一覧をクリックして**追加**します。 Visual Basic では、新しいクラスを追加し、COM 相互運用機能の新しいプロジェクトを構成します。  
  
5.  COM クラスには、プロパティ、メソッド、イベントなどのコードを追加します。  
  
6.  選択**ビルド ClassLibrary1**から、**ビルド**メニュー。 Visual Basic では、アセンブリがビルドされ、オペレーティング システムを COM オブジェクトを登録します。  
  
## <a name="creating-com-objects-without-the-com-class-template"></a>COM クラス テンプレートを使用せずに COM オブジェクトを作成します。  
 COM クラス テンプレートを使用する代わりに、手動での COM クラスを作成することもできます。 コマンドラインから作業している場合、または COM オブジェクトを定義する方法を制御する場合は、この手順をお勧めします。  
  
#### <a name="to-set-up-your-project-to-generate-a-com-object"></a>COM オブジェクトを生成するプロジェクトを設定するには  
  
1.  新しい Windows アプリケーション プロジェクトを開き、**ファイル**メニューをクリックして**NewProject**します。  
  
2.  **新しいプロジェクト** ダイアログ ボックス、**プロジェクトの種類**フィールドに、Windows が選択されていることを確認します。 選択**クラス ライブラリ**から、**テンプレート**ボックスの一覧をクリックして**OK**します。 新しいプロジェクトが表示されます。  
  
3.  **ソリューション エクスプローラー**で、プロジェクトを右クリックして、**[プロパティ]** をクリックします。 **プロジェクト デザイナー**が表示されます。  
  
4.  **[コンパイル]** タブをクリックします。  
  
5.  選択、 **COM 相互運用機能の登録**チェック ボックスをオンします。  
  
#### <a name="to-set-up-the-code-in-your-class-to-create-a-com-object"></a>COM オブジェクトを作成する、クラスのコードを設定するには  
  
1.  **ソリューション エクスプ ローラー**、ダブルクリックして**Class1.vb**そのコードを表示します。  
  
2.  クラスの名前を `ComClass1` に変更します。  
  
3.  次の定数を追加`ComClass1`します。 COM オブジェクトにして、必要なグローバル一意識別子 (GUID) の定数が格納されます。  
  
     [!code-vb[VbVbalrInterop#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#2)]  
  
4.  **[ツール]** メニューの **[GUID の作成]** をクリックします。 **[GUID の作成]** ダイアログ ボックスで、**[レジストリ形式]** をクリックし、**[コピー]** をクリックします。 **[終了]** をクリックします。  
  
5.  空の文字列を置き換える、 `ClassId` GUID を持つ削除、先頭と末尾の中かっこです。 たとえば、Guidgen によって GUID が指定されている場合は`"{2C8B0AEE-02C9-486e-B809-C780A11530FE}"`し、コードは次のように表示する必要があります。  
  
     [!code-vb[VbVbalrInterop#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#3)]  
  
6.  前の手順を繰り返して、`InterfaceId`と`EventsId`定数は、次の例のようにします。  
  
     [!code-vb[VbVbalrInterop#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#4)]  
  
    > [!NOTE]
    >  Guid は、新しいと、一意であることを確認します。それ以外の場合、COM コンポーネントは、他の COM コンポーネントと競合する可能性があります。  
  
7.  追加、`ComClass`属性を`ComClass1`、次の例のように、クラス ID、インターフェイス ID、およびイベント ID の Guid を指定します。  
  
     [!code-vb[VbVbalrInterop#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#5)]  
  
8.  COM クラスは、パラメーターなしである必要があります`Public Sub New()`コンス トラクター、またはクラスが正しく登録されません。 クラスには、パラメーターなしのコンス トラクターを追加します。  
  
     [!code-vb[VbVbalrInterop#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#6)]  
  
9. プロパティ、メソッド、およびイベントを終了して、クラスに追加、`End Class`ステートメント。 選択**ソリューションのビルド**から、**ビルド**メニュー。 Visual Basic では、アセンブリがビルドされ、オペレーティング システムを COM オブジェクトを登録します。  
  
    > [!NOTE]
    >  True の COM オブジェクトではないために、Visual Basic で生成する COM オブジェクトを他の Visual Basic アプリケーションで使用できません。 このような COM オブジェクトへの参照を追加するには、エラーが発生します。 詳細については、[.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.ComClassAttribute>
- [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)
- [チュートリアル: COM オブジェクトによる継承の実装](../../../visual-basic/programming-guide/com-interop/walkthrough-implementing-inheritance-with-com-objects.md)
- [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
- [.NET Framework アプリケーションにおける COM 相互運用性](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [相互運用性のトラブルシューティング](../../../visual-basic/programming-guide/com-interop/troubleshooting-interoperability.md)
