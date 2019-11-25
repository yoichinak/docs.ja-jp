---
title: 数値演算関数の導出
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
ms.openlocfilehash: 73cf56dd72f2baac0474d6f5c4e88228a1fe38cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349848"
---
# <a name="derived-math-functions-visual-basic"></a>数値演算関数の導出 (Visual Basic)
The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object. You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.  
  
|機能|Derived equivalents|  
|--------------|-------------------------|  
|Secant (Sec(x))|1 / Cos(x)|  
|Cosecant (Csc(x))|1 / Sin(x)|  
|Cotangent (Ctan(x))|1 / Tan(x)|  
|Inverse sine (Asin(x))|Atan(x / Sqrt(-x * x + 1))|  
|Inverse cosine (Acos(x))|Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)|  
|Inverse secant (Asec(x))|2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))|  
|Inverse cosecant (Acsc(x))|Atan(Sign(x) / Sqrt(x * x – 1))|  
|Inverse cotangent (Acot(x))|2 * Atan(1) - Atan(x)|  
|Hyperbolic sine (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|Hyperbolic cosine (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|Hyperbolic tangent (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|Hyperbolic secant (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Hyperbolic cosecant (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|Hyperbolic cotangent (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|Inverse hyperbolic sine (Asinh(x))|Log(x + Sqrt(x * x + 1))|  
|Inverse hyperbolic cosine (Acosh(x))|Log(x + Sqrt(x * x – 1))|  
|Inverse hyperbolic tangent (Atanh(x))|Log((1 + x) / (1 – x)) / 2|  
|Inverse hyperbolic secant (AsecH(x))|Log((Sqrt(-x * x + 1) + 1) / x)|  
|Inverse hyperbolic cosecant (Acsch(x))|Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)|  
|Inverse hyperbolic cotangent (Acoth(x))|Log((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>関連項目

- [数値演算関数](../../../visual-basic/language-reference/functions/math-functions.md)
