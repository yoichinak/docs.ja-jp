---
title: -nologo (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- -nologo compiler option [Visual Basic]
- banners [Visual Basic], suppressing startup
- nologo compiler option [Visual Basic]
- /nologo compiler option [Visual Basic]
ms.assetid: 25ef54b6-d676-4639-a2d2-a747a158bc07
ms.openlocfilehash: c1824e4a086ecdd4b6a776bd6894f6e003d02867
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822558"
---
# <a name="-nologo-visual-basic"></a>-nologo (Visual Basic)
コンパイル時に著作権画面を表示および情報メッセージの表示を抑制します。  
  
## <a name="syntax"></a>構文  
  
```  
-nologo  
```  
  
## <a name="remarks"></a>Remarks  
 指定した場合`-nologo`コンパイラは著作権バナーが表示されません。 既定では、`-nologo` は無効です。  
  
> [!NOTE]
>  `-nologo`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`著作権バナーは表示されません。  
  
```console
vbc -nologo t2.vb  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
