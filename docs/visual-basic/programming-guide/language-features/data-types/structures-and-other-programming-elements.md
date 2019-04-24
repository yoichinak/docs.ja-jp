---
title: 構造体およびその他のプログラミング要素 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], arrays
- procedures [Visual Basic], structures as arguments to
- objects [Visual Basic], structure elements
- arrays [Visual Basic], structure elements
- nested structures [Visual Basic]
ms.assetid: 0f849313-ccd2-4c9a-acb9-69de6751c088
ms.openlocfilehash: a943bbdec617ba6c95685df3a4fcdb36b52def22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819110"
---
# <a name="structures-and-other-programming-elements-visual-basic"></a>構造体およびその他のプログラミング要素 (Visual Basic)
構造体は、配列、オブジェクト、および手順については、相互に組み合わせて使用できます。 相互作用は、これらの要素を個別に使用するように同じ構文を使用します。  
  
> [!NOTE]
>  構造体の宣言で構造体の要素を初期化することはできません。 値は、構造体型として宣言された変数の要素にのみ割り当てることができます。  
  
## <a name="structures-and-arrays"></a>構造体と配列  
 構造体は、1 つまたは複数の要素として配列を含めることができます。 次に例を示します。  
  
```vb  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As String  
    Public purchaseDate As Date  
End Structure   
```  
  
 構造体の配列の値は、オブジェクトのプロパティにアクセスする同じ方法でアクセスします。 次に例を示します。  
  
```vb  
Dim mySystem As systemInfo  
ReDim mySystem.diskDrives(3)  
mySystem.diskDrives(0) = "1.44 MB"  
```  
  
 構造体の配列を宣言することもできます。 次に例を示します。  
  
```vb  
Dim allSystems(100) As systemInfo  
```  
  
 このデータ アーキテクチャのコンポーネントへのアクセスに同じ規則に従います。 次に例を示します。  
  
```vb  
ReDim allSystems(5).diskDrives(3)  
allSystems(5).CPU = "386SX"  
allSystems(5).diskDrives(2) = "100M SCSI"  
```  
  
## <a name="structures-and-objects"></a>構造体とオブジェクト  
 構造体には、オブジェクトを 1 つまたは複数の要素として含めることができます。 次に例を示します。  
  
```vb  
Protected Structure userInput  
    Public userName As String  
    Public inputForm As System.Windows.Forms.Form  
    Public userFileNumber As Integer  
End Structure  
```  
  
 このような宣言で特定のオブジェクト クラスを使用する必要がなく`Object`します。  
  
## <a name="structures-and-procedures"></a>構造体と手順  
 構造体は、プロシージャの引数として渡すことができます。 次に例を示します。  
  
```vb  
Public currentCPUName As String = "700MHz Pentium compatible"  
Public currentMemorySize As Long = 256  
Public Sub fillSystem(ByRef someSystem As systemInfo)  
    someSystem.cPU = currentCPUName  
    someSystem.memory = currentMemorySize  
    someSystem.purchaseDate = Now  
End Sub  
```  
  
 前の例は、構造体を渡して*参照によって*プロシージャを呼び出し元のコードの変更が反映されるように、その要素を変更することができます。 このような変更に対して構造体を保護する場合は、値によって渡します。  
  
 構造体を返すこともできます、`Function`プロシージャ。 次に例を示します。  
  
```vb  
Dim allSystems(100) As systemInfo  
Function findByDate(ByVal searchDate As Date) As systemInfo  
    Dim i As Integer  
    For i = 1 To 100  
        If allSystems(i).purchaseDate = searchDate Then Return allSystems(i)  
    Next i  
   ' Process error: system with desired purchase date not found.  
End Function  
```  
  
## <a name="structures-within-structures"></a>構造内の構造  
 構造体は、その他の構造を含めることができます。 次に例を示します。  
  
```vb  
Public Structure driveInfo  
    Public type As String  
    Public size As Long  
End Structure  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public diskDrives() As driveInfo  
    Public purchaseDate As Date  
End Structure  
```  
  
```vb  
Dim allSystems(100) As systemInfo  
ReDim allSystems(1).diskDrives(3)  
allSystems(1).diskDrives(0).type = "Floppy"  
```  
  
 別のモジュールで定義された構造内の 1 つのモジュールで定義された構造をカプセル化するのにこの手法を使用することもできます。  
  
 構造体は、任意の深さを他の構造体を含めることができます。  
  
## <a name="see-also"></a>関連項目

- [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [方法: 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [構造体変数](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
