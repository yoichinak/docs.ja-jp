---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793914"
---
# <a name="-main"></a>-main
`Sub Main` プロシージャを格納するクラスまたはモジュールを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>引数  
 `location`  
 必須。 クラスまたはを含むモジュールの名前、`Sub Main`プログラムの開始時に呼び出されるプロシージャです。 フォームのことが考えられます **-メイン: モジュール**または **-main:namespace.module**します。  
  
## <a name="remarks"></a>Remarks  
 実行可能ファイルまたは Windows 実行可能プログラムを作成するときに、このオプションを使用します。 場合、 **-メイン**オプションを省略すると、コンパイラは、有効な共有の検索`Sub Main`ですべてのパブリック クラスとモジュール。  
  
 参照してください[Visual basic の Main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)のさまざまな形式の詳細については、`Main`プロシージャ。  
  
 ときに`location`から継承するクラスは、 <xref:System.Windows.Forms.Form>、コンパイラは、既定値を用意`Main`クラスにない場合に、アプリケーションを開始するプロシージャ`Main`プロシージャ。 これにより、開発環境で作成したコマンドラインでコードをコンパイルできます。  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>設定 - Visual Studio 統合開発環境で主に  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. **[アプリケーション]** タブをクリックします。  
  
3. 確認、**アプリケーション フレームワークを有効にする**チェック ボックスをオンします。  
  
4. 値を変更、**スタートアップ オブジェクト**ボックス。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`と`T3.vb`を指定している、`Sub Main`手順が記載されて、`Test2`クラス。  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-ターゲット (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Visual Basic の main プロシージャ](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
