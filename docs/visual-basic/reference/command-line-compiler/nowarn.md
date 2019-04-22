---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828213"
---
# <a name="-nowarn"></a>-nowarn
警告を生成するコンパイラの機能を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`numberList`|省略可能です。 コンパイラはしないようにする警告の ID 番号のコンマ区切りリスト。 警告の Id が指定されていない場合は、すべての警告が抑制されます。|  
  
## <a name="remarks"></a>Remarks  
 `-nowarn`オプションと、コンパイラの警告を生成しません。 個々 の警告を抑制するのに警告の ID を指定します、`-nowarn`コロンに続くオプション。 複数の警告番号をコンマで区切ります。  
  
 警告 id の数値の一部だけを指定する必要があります。 たとえば、BC42024、未使用のローカル変数の警告を抑制する場合は、指定`-nowarn:42024`します。  
  
 警告の ID 番号の詳細については、次を参照してください。 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
|Visual Studio 統合開発環境で-nowarn を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.選択、**すべての警告を無効にする**すべての警告を無効にする チェック ボックス。<br />     または<br />     特定の警告を無効にするには、 **None**警告の横にあるドロップダウン リストから。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`すべての警告は表示されません。  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`未使用のローカル変数 (42024) の警告は表示されません。  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
