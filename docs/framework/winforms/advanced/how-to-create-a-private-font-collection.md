---
title: '方法: プライベート フォント コレクションを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- private font collections [Windows Forms], creating
- fonts [Windows Forms], creating private collections
ms.assetid: 6533d5e5-a8dc-4b76-9fc4-3bf75c8b9212
ms.openlocfilehash: f78d48c88b72388676f5e7ae963b98d8f1b4beac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937835"
---
# <a name="how-to-create-a-private-font-collection"></a>方法: プライベート フォント コレクションを作成する
<xref:System.Drawing.Text.PrivateFontCollection>クラスから継承、<xref:System.Drawing.Text.FontCollection>抽象基本クラス。 使用することができます、<xref:System.Drawing.Text.PrivateFontCollection>具体的には、アプリケーションのフォントのセットを保持するオブジェクト。 プライベート フォント コレクションには、インストールされているシステム フォントだけでなく、コンピューターにインストールされていないフォントを含めることができます。 プライベート フォント コレクションには、フォント ファイルを追加するには、呼び出し、<xref:System.Drawing.Text.PrivateFontCollection.AddFontFile%2A>のメソッドを<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
 <xref:System.Drawing.Text.FontCollection.Families%2A>のプロパティを<xref:System.Drawing.Text.PrivateFontCollection>オブジェクトには配列が含まれています<xref:System.Drawing.FontFamily>オブジェクト。  
  
 プライベート フォント コレクション内のフォント ファミリの数は必ずしもコレクションに追加されたフォント ファイルの数と同じです。 たとえば、ArialBd.tff、Times.tff、および TimesBd.tff ファイルをコレクションに追加するとします。 ありますが、3 つのファイル、コレクション内の 2 つだけのファミリ Times.tff と TimesBd.tff 同じファミリに属しているためです。  
  
## <a name="example"></a>例  
 次の例では、次の 3 つのフォント ファイルを<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
- C:\\*systemroot*\Fonts\Arial.tff (Arial、正規表現)  
  
- C:\\*systemroot*\Fonts\CourBI.tff (Courier New、太字斜体)  
  
- C:\\*systemroot*\Fonts\TimesBd.tff (Times New Roman, bold)  
  
 コードの配列を取得する<xref:System.Drawing.FontFamily>オブジェクトから、<xref:System.Drawing.Text.FontCollection.Families%2A>のプロパティ、<xref:System.Drawing.Text.PrivateFontCollection>オブジェクト。  
  
 各<xref:System.Drawing.FontFamily>コードでは、コレクション内のオブジェクト、<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>するさまざまなスタイル (標準、太字、斜体、太字、斜体、下線、取り消し線) が使用できるかどうかを判断するメソッド。 渡される引数、<xref:System.Drawing.FontFamily.IsStyleAvailable%2A>メソッドのメンバーである、<xref:System.Drawing.FontStyle>列挙体。  
  
 指定されたファミリ/スタイルの組み合わせがある場合、<xref:System.Drawing.Font>そのファミリとスタイルを使用してオブジェクトを構築します。 渡される最初の引数、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクターは、フォント ファミリ名 (いない、<xref:System.Drawing.FontFamily>オブジェクトの他のバリエーションの場合と同様、<xref:System.Drawing.Font.%23ctor%2A>コンス トラクター)。 後に、<xref:System.Drawing.Font>オブジェクトが構築されたに渡される、<xref:System.Drawing.Graphics.DrawString%2A>のメソッド、<xref:System.Drawing.Graphics>スタイルの名前と共に、ファミリ名を表示するクラス。  
  
 次のコードの出力は次の図に示すように出力になります。  
  
 ![さまざまなフォントでテキストを示すスクリーン ショット。](./media/how-to-create-a-private-font-collection/various-fonts-text-output.png)  
  
 次のコード例では、プライベート フォント コレクションに追加された) Arial.tff は、Arial 標準スタイルのフォント ファイルです。 ただし、プログラムの出力が Arial フォント ファミリの標準以外の複数の使用可能なスタイルを表示することに注意してください。 だ[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]標準スタイルから太字、斜体、および太字斜体スタイルをシミュレートすることができます。 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] 下線や標準のスタイルから取り消し線の生成もできます。  
  
 同様に、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]太字または斜体のスタイルのいずれかから太字斜体のスタイルをシミュレートすることができます。 プログラムの出力が TimesBd.tff (Times New Roman、太字) が唯一にもかかわらず太字斜体スタイルが回ファミリに使用できることを示しています、コレクション内の回ファイル。  
  
 [!code-csharp[System.Drawing.FontsAndText#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.FontsAndText#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 前の例は、Windows フォームで使用するために設計されています。 また必要が<xref:System.Windows.Forms.PaintEventArgs> `e`、はのパラメーター<xref:System.Windows.Forms.PaintEventHandler>します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Drawing.Text.PrivateFontCollection>
- [フォントとテキストの使用](using-fonts-and-text.md)
