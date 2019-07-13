---
title: '#ExternalSource ディレクティブ (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- '#Externalsource'
- '#ExternalSource'
- vb.ExternalSource
- Externalsource
- vb.#ExternalSource
- ExternalSource
helpviewer_keywords:
- ExternalSource directive (#ExternalSource)
- '#ExternalSource directive'
ms.assetid: 243bc6a2-34c3-4eeb-a776-9fd2bf988149
ms.openlocfilehash: 39e6963c97340daab3f0ab7ad6860695f1f6c135
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747045"
---
# <a name="externalsource-directive"></a>#ExternalSource ディレクティブ
ソース コードの特定の行とソース外部のテキスト間のマッピングを示します。  
  
## <a name="syntax"></a>構文  
  
```  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>指定項目  
 `StringLiteral`  
 外部ソースへのパス。  
  
 `IntLiteral`  
 外部ソースの最初の行の行番号。  
  
 `LogicalLine`  
 行を外部ソースでエラーが発生します。  
  
 `#End ExternalSource`  
 `#ExternalSource` ブロックを終了します。  
  
## <a name="remarks"></a>Remarks  
 このディレクティブは、コンパイラと、デバッガーでのみ使用されます。  
  
 ソース ファイルには、ソース ファイル内のコードの特定の行と、.aspx ファイルなど、ソースの外部のテキスト間のマッピングを示す外部ソース ディレクティブを含めることができます。 指定されたソース コードでは、コンパイル中にエラーが発生する場合は、外部ソースからのものとして識別されます。  
  
 外部ソース ディレクティブは、コンパイルに影響を与えるありませんし、入れ子にすることはできません。 内部使用のアプリケーションのみが用意されています。  
  
## <a name="see-also"></a>関連項目

- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
