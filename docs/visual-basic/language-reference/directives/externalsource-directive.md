---
title: '#ExternalSource ディレクティブ'
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
ms.openlocfilehash: fa0a40827c1b3865b90c7d796ea4dd364774e1c4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343830"
---
# <a name="externalsource-directive"></a>#ExternalSource ディレクティブ

ソース コードの特定の行と、ソースの外部のテキストとの間のマッピングを示します。  
  
## <a name="syntax"></a>構文  
  
```vb  
#ExternalSource( StringLiteral , IntLiteral )  
    [ LogicalLine+ ]  
#End ExternalSource  
```  
  
## <a name="parts"></a>指定項目  

 `StringLiteral`  
 外部ソースへのパスです。  
  
 `IntLiteral`  
 外部ソースの最初の行の行番号です。  
  
 `LogicalLine`  
 外部ソースでエラーが発生した行です。  
  
 `#End ExternalSource`  
 `#ExternalSource` ブロックを終了します。  
  
## <a name="remarks"></a>Remarks  

 このディレクティブは、コンパイラとデバッガーによってのみ使用されます。  
  
 ソース ファイルには、外部ソース ディレクティブを含めることができます。これは、ソース ファイル内の特定のコード行と、.aspx ファイルなどのソースの外部のテキストとの間のマッピングを示します。 コンパイル時に指定されたソース コードでエラーが発生した場合、外部ソースからのものとして識別されます。  
  
 外部ソース ディレクティブはコンパイルには影響しません。また、入れ子にすることはできません。 これらはアプリケーションによる内部使用のみを目的としています。  
  
## <a name="see-also"></a>関連項目

- [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
