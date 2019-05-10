---
title: 変数 '<variablename>' は、囲まれたブロック内の変数を非表示にします。
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 36fe543dd4546c6fe930f259a55cea856917370f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662666"
---
# <a name="variable-variablename-hides-a-variable-in-an-enclosing-block"></a>変数 '\<variablename >'、それを囲むブロック内の変数を非表示になります
ブロックで囲まれた変数では、別のローカル変数と同じ名前を持ちます。  
  
 **エラー ID:** BC30616  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- 囲まれたブロック内の変数の名前を変更して、他の任意のローカル変数と同じではないようにします。 例えば:  
  
    ```  
    Dim a, b, x As Integer  
    If a = b Then  
       Dim y As Integer = 20 ' Uniquely named block variable.  
    End If  
    ```  
  
- このエラーの一般的な原因は、使用`Catch e As Exception`イベント ハンドラーの内部。 この場合は、名前、`Catch`ブロック変数`ex`なく`e`します。  
  
- このエラーのもう 1 つの一般的な原因は内で宣言されたローカル変数にアクセスしようとする`Try`個別のブロック`Catch`ブロック。 これを修正するには、外部変数を宣言、`Try...Catch...Finally`構造体。  
  
## <a name="see-also"></a>関連項目

- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
