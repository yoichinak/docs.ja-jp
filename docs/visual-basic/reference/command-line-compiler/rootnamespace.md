---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: ff4b1729f1b9fb1d698b4b5b1e3711ce3d27b4db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639036"
---
# <a name="-rootnamespace"></a>-rootnamespace
すべての型宣言に対して名前空間を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`namespace`|現在のプロジェクトのすべての型宣言を囲む名前空間の名前。|  
  
## <a name="remarks"></a>Remarks  
 使用して、Visual Studio 統合開発環境で作成したプロジェクトをコンパイルする Visual Studio の実行可能ファイル (Devenv.exe) を使用する場合`-rootnamespace`の値を指定する、<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>プロパティ。 参照してください[Devenv コマンド ライン スイッチ](/visualstudio/ide/reference/devenv-command-line-switches)詳細についてはします。  
  
 共通言語ランタイム MSIL 逆アセンブラーを使用して (`Ildasm.exe`) を出力ファイルの名前空間の名前を表示します。  
  
|Visual Studio 統合開発環境で-rootnamespace を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**ルート Namespace**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`と名前空間のすべての型宣言を囲む`mynamespace`します。  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm.exe (IL 逆アセンブラー)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
