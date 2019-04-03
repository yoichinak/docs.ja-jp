---
title: ファイルにこれ以上データがありません。
ms.date: 07/20/2015
f1_keywords:
- vbrID62
ms.assetid: 65292704-6e7d-4622-9f50-eb655a59b016
ms.openlocfilehash: 63b099144b9da601a7b52a738f5a3173097ae257
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813159"
---
# <a name="input-past-end-of-file"></a>ファイルにこれ以上データがありません。
いずれか、`Input`ステートメントは空であるファイルまたはすべてのデータを使用すると、またはを使用していずれかから読み取って、`EOF`バイナリへのアクセスのファイルを使用して関数を開きます。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  使用して、`EOF`する直前に機能、`Input`ステートメント ファイルの終わりを検出します。  
  
2.  バイナリ アクセスのため、ファイルを開く場合は、使用`Seek`と`Loc`します。  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.FileSystem.Input%2A>
- <xref:Microsoft.VisualBasic.FileSystem.EOF%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Seek%2A>
- <xref:Microsoft.VisualBasic.FileSystem.Loc%2A>
