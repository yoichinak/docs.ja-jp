---
title: 配列のトラブルシューティング
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting arrays
- arrays [Visual Basic], initialization errors
- troubleshooting Visual Basic, arrays
- arrays [Visual Basic], compilation errors
- arrays [Visual Basic], declaration errors
- arrays [Visual Basic], troubleshooting
ms.assetid: f4e971c7-c0a4-4ed7-a77a-8d71039f266f
ms.openlocfilehash: 3c50c68c2a39aa04cff2dd43b5dfde709aec290f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349065"
---
# <a name="troubleshooting-arrays-visual-basic"></a>配列のトラブルシューティング (Visual Basic)
This page lists some common problems that can occur when working with arrays.  
  
## <a name="compilation-errors-declaring-and-initializing-an-array"></a>Compilation Errors Declaring and Initializing an Array  
 Compilation errors can arise from misunderstanding of the rules for declaring, creating, and initializing arrays. The most common causes of errors are the following:  
  
- Supplying a [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) clause after specifying dimension lengths in the array variable declaration. The following code lines show invalid declarations of this type.  
  
     `Dim INVALIDsingleDimByteArray(2) As Byte = New Byte()`  
  
     `Dim INVALIDtwoDimShortArray(1, 1) As Short = New Short(,)`  
  
     `Dim INVALIDjaggedByteArray(1)() As Byte = New Byte()()`  
  
- Specifying dimension lengths for more than the top-level array of a jagged array. The following code line shows an invalid declaration of this type.  
  
     `Dim INVALIDjaggedByteArray(1)(1) As Byte`  
  
- Omitting the `New` keyword when specifying the element values. The following code line shows an invalid declaration of this type.  
  
     `Dim INVALIDoneDimShortArray() As Short = Short() {0, 1, 2, 3}`  
  
- Supplying a `New` clause without braces (`{}`). The following code lines show invalid declarations of this type.  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte()`  
  
     `Dim INVALIDsingleDimByteArray() As Byte = New Byte(2)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(,)`  
  
     `Dim INVALIDtwoDimShortArray(,) As Short = New Short(1, 1)`  
  
## <a name="accessing-an-array-out-of-bounds"></a>Accessing an Array Out of Bounds  
 The process of initializing an array assigns an upper bound and a lower bound to each dimension. Every access to an element of the array must specify a valid index, or subscript, for every dimension. If any index is below its lower bound or above its upper bound, an <xref:System.IndexOutOfRangeException> exception results. The compiler cannot detect such an error, so an error occurs at run time.  
  
### <a name="determining-bounds"></a>Determining Bounds  
 If another component passes an array to your code, for example as a procedure argument, you do not know the size of that array or the lengths of its dimensions. You should always determine the upper bound for every dimension of an array before you attempt to access any elements. If the array has been created by some means other than a Visual Basic `New` clause, the lower bound might be something other than 0, and it is safest to determine that lower bound as well.  
  
### <a name="specifying-the-dimension"></a>Specifying the Dimension  
 When determining the bounds of a multidimensional array, take care how you specify the dimension. The `dimension` parameters of the <xref:System.Array.GetLowerBound%2A> and <xref:System.Array.GetUpperBound%2A> methods are 0-based, while the `Rank` parameters of the Visual Basic <xref:Microsoft.VisualBasic.Information.LBound%2A> and <xref:Microsoft.VisualBasic.Information.UBound%2A> functions are 1-based.  
  
## <a name="see-also"></a>関連項目

- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [方法: Visual Basic で配列変数を初期化する](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)
