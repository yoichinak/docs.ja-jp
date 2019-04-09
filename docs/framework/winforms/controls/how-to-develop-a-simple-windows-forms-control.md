---
title: '方法: シンプルな Windows フォーム コントロールを開発する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms]
- custom controls [Windows Forms], creating simple controls using code
- Control class [Windows Forms], Windows Forms
ms.assetid: 86cbe435-45b7-4cb4-9b5a-47418369758d
ms.openlocfilehash: 845e550d0e784568723acbe098fabb2a555ce9b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59089370"
---
# <a name="how-to-develop-a-simple-windows-forms-control"></a>方法: シンプルな Windows フォーム コントロールを開発する
ここでは、カスタム Windows フォーム コントロールの主な作成手順を紹介します。 このチュートリアルで開発された単純なコントロールでの配置は、その<xref:System.Windows.Forms.Control.Text%2A>プロパティを変更します。 イベントを発生させたり処理したりすることはありません。  
  
### <a name="to-create-a-simple-custom-control"></a>シンプルなカスタム コントロールを作成するには  
  
1.  <xref:System.Windows.Forms.Control?displayProperty=nameWithType> から派生するクラスを定義します。  
  
    ```vb  
    Public Class FirstControl  
       Inherits Control  
  
    End Class  
    ```  
  
    ```csharp  
    public class FirstControl:Control {}  
    ```  
  
2.  プロパティを定義します  (コントロールから多くのプロパティを継承するためのプロパティを定義する必要はありません、<xref:System.Windows.Forms.Control>追加のプロパティを定義して一般に、クラスが、ほとんどのカスタム コントロールです)。次のコード フラグメントは、という名前のプロパティを定義します。`TextAlignment`を`FirstControl`の表示形式を使用して、<xref:System.Windows.Forms.Control.Text%2A>プロパティから継承<xref:System.Windows.Forms.Control>します。 プロパティの定義の詳細については、「[プロパティの概要](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/65zdfbdt(v%3dvs.120))」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#3)]
     [!code-vb[System.Windows.Forms.FirstControl#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#3)]  
  
     コントロールの視覚的な表示を変更するプロパティを設定するときに呼び出す必要があります、<xref:System.Windows.Forms.Control.Invalidate%2A>コントロールを再描画するメソッド。 <xref:System.Windows.Forms.Control.Invalidate%2A> 基本クラスで定義されて<xref:System.Windows.Forms.Control>します。  
  
3.  保護されたオーバーライド<xref:System.Windows.Forms.Control.OnPaint%2A>から継承されたメソッド<xref:System.Windows.Forms.Control>をコントロールにレンダリング ロジックを提供します。 オーバーライドしていない場合<xref:System.Windows.Forms.Control.OnPaint%2A>コントロールは描画できません。 次のコード フラグメントで、<xref:System.Windows.Forms.Control.OnPaint%2A>メソッドが表示されます、<xref:System.Windows.Forms.Control.Text%2A>プロパティから継承<xref:System.Windows.Forms.Control>によって指定された配置と、`alignmentValue`フィールド。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#4)]
     [!code-vb[System.Windows.Forms.FirstControl#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#4)]  
  
4.  コントロールの属性を指定します。 ビジュアル デザイナーでは、デザイン時に属性を使用することで、コントロール、コントロールのプロパティ、およびイベントを適切に表示します。 次のコード フラグメントでは、属性が `TextAlignment` プロパティに適用されます。 Visual Studio などのデザイナーで、 <xref:System.ComponentModel.CategoryAttribute.Category%2A> (コード フラグメントで示されている) 属性が論理カテゴリの下に表示するプロパティ。 <xref:System.ComponentModel.DescriptionAttribute.Description%2A>属性によって、わかりやすい文字列の下部に表示される、**プロパティ**ウィンドウと、`TextAlignment`プロパティが選択されています。 属性の詳細については、「[コンポーネントのデザイン時属性](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/tk67c2t8(v=vs.120))」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.FirstControl#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#5)]
     [!code-vb[System.Windows.Forms.FirstControl#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#5)]  
  
5.  (省略可能) コントロールに対してリソースを指定します。 コントロールに対してビットマップなどのリソースを指定するには、コンパイラ オプション (C# の場合は `/res`) を使用して、リソースをコントロールと共にパッケージ化します。 実行時に、リソース取得できるのメソッドを使用して、<xref:System.Resources.ResourceManager>クラス。 リソースの作成と使用の詳細については、「[デスクトップ アプリケーションのリソース](../../resources/index.md)」を参照してください。  
  
6.  コンパイルしてコントロールを配置します。 `FirstControl,` をコンパイルして配置するには、次の手順を実行します。  
  
    1.  次のサンプル コードをソース ファイル (FirstControl.cs、FirstControl.vb など) に保存します。  
  
    2.  ソース コードをコンパイルして、アセンブリを生成し、アプリケーションのディレクトリに保存します。 それには、ソース ファイルが格納されているディレクトリで次のコマンドを実行します。  
  
        ```console  
        vbc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.vb  
        ```  
  
        ```console 
        csc -t:library -out:[path to your application's directory]/CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll FirstControl.cs  
        ```  
  
         `/t:library` コンパイラ オプションは、作成しているアセンブリが (実行可能ファイルではなく) ライブラリであることをコンパイラに伝えます。 `/out` オプションでは、アセンブリの名前とパスを指定します。 `/r` オプションでは、コードが参照するアセンブリの名前を指定します。 この例では、ご自身のアプリケーションのみが使用できるプライベート アセンブリを作成します。 このため、アセンブリはご自身のアプリケーションのディレクトリに保存する必要があります。 配布用コントロールのパッケージ化と配置の詳細については、[配置](../../deployment/index.md)に関するページをご覧ください。  
  
 次のサンプルは、`FirstControl` のコードを示しています。 このコントロールは、`CustomWinControls` 名前空間に囲まれています。 名前空間では、関連する型を論理的にグループ化できます。 コントロールは、新しい名前空間または既存の名前空間に作成できます。 C# では、`using` 宣言 (Visual Basic の場合は `Imports`) を使用すると、名前空間から型へアクセスするときに、型の完全修飾名を使用する必要はありません。 次の例では、`using`宣言により、クラスにアクセスするためのコード<xref:System.Windows.Forms.Control>から<xref:System.Windows.Forms?displayProperty=nameWithType>単に<xref:System.Windows.Forms.Control>完全修飾名を使用することではなく<xref:System.Windows.Forms.Control?displayProperty=nameWithType>します。  
  
 [!code-csharp[System.Windows.Forms.FirstControl#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/FirstControl.cs#1)]
 [!code-vb[System.Windows.Forms.FirstControl#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/FirstControl.vb#1)]  
  
## <a name="using-the-custom-control-on-a-form"></a>フォームでのカスタム コントロールの使用  
 `FirstControl` を使用するシンプルなフォームの例を次に示します。 この例では、`FirstControl` のインスタンスを 3 つ作成します。それぞれのインスタンスで、`TextAlignment` プロパティに異なる値が設定されます。  
  
#### <a name="to-compile-and-run-this-sample"></a>このサンプルをコンパイルして実行するには  
  
1.  このサンプルをコンパイルして実行するには、次に示すサンプルのコードをソース ファイル (SimpleForm.cs または SimpleForms.vb) に保存します。  
  
2.  ソース ファイルが格納されているディレクトリから次のコマンドを実行して、ソース コードを実行可能アセンブリにコンパイルします。  
  
    ```console  
    vbc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.vb  
    ```  
  
    ```console 
    csc -r:CustomWinControls.dll -r:System.dll -r:System.Windows.Forms.dll -r:System.Drawing.dll SimpleForm.cs  
    ```  
  
     CustomWinControls.dll は、クラスを含むアセンブリ`FirstControl`します。 フォームがアセンブリにアクセスできるように、そのアセンブリはソース ファイル (SimpleForm.cs または SimpleForms.vb) と同じディレクトリに格納されている必要があります。  
  
3.  次のコマンドで SimpleForm.exe を実行します。  
  
    ```console
    SimpleForm  
    ```  
  
 [!code-csharp[System.Windows.Forms.FirstControl#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/CS/SimpleForm.cs#10)]
 [!code-vb[System.Windows.Forms.FirstControl#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FirstControl/VB/SimpleForm.vb#10)]  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロールのプロパティ](properties-in-windows-forms-controls.md)
- [Windows フォーム コントロールのイベント](events-in-windows-forms-controls.md)
