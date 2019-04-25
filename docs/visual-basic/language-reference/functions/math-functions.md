---
title: 数値演算関数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- math functions, Visual Basic
- arithmetic operations, math functions
- math routines
- Atn function
ms.assetid: 4d2d82e7-6924-42fe-a4a7-b4dd5bebbd0c
ms.openlocfilehash: e5f87a8e367e8c9df65b979fea3781b42ee3ce83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824963"
---
# <a name="math-functions-visual-basic"></a>数値演算関数 (Visual Basic)
メソッド、<xref:System.Math?displayProperty=nameWithType>クラスは三角関数演算、対数演算、およびその他の一般的な数学関数を提供します。  
  
## <a name="remarks"></a>Remarks  
 次の表に、メソッドの<xref:System.Math?displayProperty=nameWithType>クラス。 Visual Basic プログラムでこれらを使用することができます。  
  
|.NET メソッド|説明|  
|---------------------------|-----------------|  
|<xref:System.Math.Abs%2A>|絶対値を返します。|  
|<xref:System.Math.Acos%2A>|コサインが指定数となる角度を返します。|  
|<xref:System.Math.Asin%2A>|サインが指定数となる角度を返します。|  
|<xref:System.Math.Atan%2A>|タンジェントが指定数となる角度を返します。|  
|<xref:System.Math.Atan2%2A>|タンジェントが 2 つの指定された数の商である角度を返します。|  
|<xref:System.Math.BigMul%2A>|2 つの 32 ビット数値の完全な積を返します。|  
|<xref:System.Math.Ceiling%2A>|指定した以上である最小の整数値を返します`Decimal`または`Double`します。|  
|<xref:System.Math.Cos%2A>|指定された角度のコサインを返します。|  
|<xref:System.Math.Cosh%2A>|指定された角度のハイパーボリック コサインを返します。|  
|<xref:System.Math.DivRem%2A>|2 32 ビットまたは 64 ビット符号付き整数の商を返し、出力パラメーターの剰余を返します。|  
|<xref:System.Math.Exp%2A>|指定した累乗された e (自然対数の底) を返します。|  
|<xref:System.Math.Floor%2A>|指定した小さい最大整数を返します`Decimal`または`Double`数。|  
|<xref:System.Math.IEEERemainder%2A>|指定された数の剰余をもう 1 つの指定された数値の除算の結果を返します。|  
|<xref:System.Math.Log%2A>|指定した基数では、指定した数の自然 (底 e) 対数または指定した数の対数を返します。|  
|<xref:System.Math.Log10%2A>|指定した数の底 10 の対数を返します。|  
|<xref:System.Math.Max%2A>|2 つの数値のうち、大きい方を返します。|  
|<xref:System.Math.Min%2A>|2 つの数のうち、小さい方を返します。|  
|<xref:System.Math.Pow%2A>|指定の数値を指定した値で累乗した値を返します。|  
|<xref:System.Math.Round%2A>|返します、`Decimal`または`Double`値には、最も近い整数値または指定された数の桁の小数部が丸められます。|  
|<xref:System.Math.Sign%2A>|返します、`Integer`数値の符号を示す値。|  
|<xref:System.Math.Sin%2A>|指定された角度のサインを返します。|  
|<xref:System.Math.Sinh%2A>|指定された角度のハイパーボリック サインを返します。|  
|<xref:System.Math.Sqrt%2A>|指定された数値の平方根を返します。|  
|<xref:System.Math.Tan%2A>|指定された角度のタンジェントを返します。|  
|<xref:System.Math.Tanh%2A>|指定された角度のハイパーボリック タンジェントを返します。|  
|<xref:System.Math.Truncate%2A>|指定の整数部を計算`Decimal`または`Double`数。|  
  
 修飾なしのこれらの関数を使用するインポート、<xref:System.Math?displayProperty=nameWithType>ソース ファイルの先頭に次のコードを追加して、プロジェクトに名前空間。  
  
```vb
Imports System.Math  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Abs%2A>のメソッド、<xref:System.Math>数値の絶対値を計算するクラス。  
  
```vb
' Returns 50.3.  
Dim MyNumber1 As Double = Math.Abs(50.3)  
' Returns 50.3.  
Dim MyNumber2 As Double = Math.Abs(-50.3)  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Atan%2A>のメソッド、 <xref:System.Math> pi の値を計算するクラス。  
  
```vb
Public Function GetPi() As Double  
    ' Calculate the value of pi.  
    Return 4.0 * Math.Atan(1.0)  
End Function  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Cos%2A>のメソッド、<xref:System.Math>クラス角度のコサインを返します。  
  
```vb
Public Function Sec(ByVal angle As Double) As Double  
    ' Calculate the secant of angle, in radians.  
    Return 1.0 / Math.Cos(angle)  
End Function  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Exp%2A>のメソッド、<xref:System.Math>クラスを e の累乗を返します。  
  
```vb
Public Function Sinh(ByVal angle As Double) As Double  
    ' Calculate hyperbolic sine of an angle, in radians.  
    Return (Math.Exp(angle) - Math.Exp(-angle)) / 2.0  
End Function  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Log%2A>のメソッド、<xref:System.Math>クラス数値の自然対数を返します。  
  
```vb
Public Function Asinh(ByVal value As Double) As Double  
    ' Calculate inverse hyperbolic sine, in radians.  
    Return Math.Log(value + Math.Sqrt(value * value + 1.0))  
End Function  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Round%2A>のメソッド、<xref:System.Math>に最も近い整数に数値を丸めるクラス。  
  
```vb
' Returns 3.  
Dim MyVar2 As Double = Math.Round(2.8)  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Sign%2A>のメソッド、<xref:System.Math>クラスを数値の符号を調べます。  
  
```vb
' Returns 1.  
Dim MySign1 As Integer = Math.Sign(12)  
' Returns -1.  
Dim MySign2 As Integer = Math.Sign(-2.4)  
' Returns 0.  
Dim MySign3 As Integer = Math.Sign(0)  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Sin%2A>のメソッド、<xref:System.Math>クラス角度のサインを返します。  
  
```vb
Public Function Csc(ByVal angle As Double) As Double  
    ' Calculate cosecant of an angle, in radians.  
    Return 1.0 / Math.Sin(angle)  
End Function  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Sqrt%2A>のメソッド、<xref:System.Math>数値の平方根を計算するクラス。  
  
```vb
' Returns 2.  
Dim MySqr1 As Double = Math.Sqrt(4)  
' Returns 4.79583152331272.  
Dim MySqr2 As Double = Math.Sqrt(23)  
' Returns 0.  
Dim MySqr3 As Double = Math.Sqrt(0)  
' Returns NaN (not a number).  
Dim MySqr4 As Double = Math.Sqrt(-4)  
```  
  
## <a name="example"></a>例  
 この例では、<xref:System.Math.Tan%2A>のメソッド、<xref:System.Math>クラス角度のタンジェントを返します。  
  
```vb
Public Function Ctan(ByVal angle As Double) As Double  
    ' Calculate cotangent of an angle, in radians.  
    Return 1.0 / Math.Tan(angle)  
End Function  
```  
  
## <a name="requirements"></a>必要条件  
 **クラス:** <xref:System.Math>  
  
 **名前空間:** <xref:System>  
  
 **アセンブリ:** mscorlib (mscorlib.dll 内)  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.VBMath.Rnd%2A>
- <xref:Microsoft.VisualBasic.VBMath.Randomize%2A>
- <xref:System.Double.NaN>
- [数値演算関数の導出](../../../visual-basic/language-reference/keywords/derived-math-functions.md)
- [算術演算子](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
