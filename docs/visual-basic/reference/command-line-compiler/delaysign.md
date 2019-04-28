---
title: -delaysign
ms.date: 03/10/2018
helpviewer_keywords:
- delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
- -delaysign compiler option [Visual Basic]
ms.assetid: c76e61a4-1884-4252-9fb2-377f99caa690
ms.openlocfilehash: 770dcad385c522a548a0c6fd3b6ef02dfbac82f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649713"
---
# <a name="-delaysign"></a>-delaysign
アセンブリに完全に署名するか、部分的に署名するかを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-delaysign[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 任意。 完全署名されたアセンブリを作成する場合は、`-delaysign-` を使用します。 使用`-delaysign+`かどうかは、署名のハッシュのアセンブリと予約のスペースで公開キーを配置します。 既定値は `-delaysign-` です。  
  
## <a name="remarks"></a>Remarks  
 `-delaysign`オプションも何も起こりません併用しない限り、 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)または[-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)します。  
  
 アセンブリに完全に署名するように指定すると、コンパイラはマニフェスト (アセンブリ メタデータ) を含むファイルをハッシュし、秘密キーでそのハッシュに署名します。 結果として得られるデジタル署名は、マニフェストを含むファイルに格納されます。 アセンブリに遅延署名がある場合、コンパイラはいないコンピューティングし、署名を後で追加できるように、ファイルに署名が予約領域を格納します。  
  
 たとえばを使用して`-delaysign+`組織内の開発者は、テスト担当者をグローバル アセンブリ キャッシュに登録して使用するアセンブリの署名のないテスト バージョンを配布できます。 アセンブリでの作業が完了したら、組織の秘密キーの責任者は、アセンブリに完全署名します。 この区分は、すべての開発者に、アセンブリで作業しながら漏洩から組織の秘密キーを保護します。  
  
 参照してください[の作成と using strong-named Assemblies](../../../framework/app-domains/create-and-use-strong-named-assemblies.md)アセンブリへの署名の詳細についてはします。  
  
### <a name="to-set--delaysign-in-the-visual-studio-integrated-development-environment"></a>Visual Studio 統合開発環境で-delaysign を設定するには  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。   
  
2. **[署名]** タブをクリックします。  
  
3. 値を設定、**遅延署名のみ**ボックス。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)
- [-keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
