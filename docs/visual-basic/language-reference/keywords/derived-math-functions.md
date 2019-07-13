---
title: 数値演算関数の導出 (Visual Basic)
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
ms.openlocfilehash: 0d0606c52d1d50fcc2fd8eea3ad2851c95b18a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801895"
---
# <a name="derived-math-functions-visual-basic"></a>数値演算関数の導出 (Visual Basic)
次の表はの組み込みの数学関数から派生可能な非組み込みの数学関数、<xref:System.Math?displayProperty=nameWithType>オブジェクト。 組み込みの数学関数を追加することでアクセスできる`Imports System.Math`ファイルまたはプロジェクトにします。  
  
|関数|対応する派生|  
|--------------|-------------------------|  
|Secant (Sec(x))|1 / Cos(x)|  
|余割 (Csc(x))|1 / Sin(x)|  
|コタンジェント (Ctan(x))|1 / Tan(x)|  
|逆正弦 (Asin(x))|Atan(x / Sqrt(-x * x + 1))|  
|逆コサイン (Acos(x))|Atan (-x/Sqrt (-x * x + 1)) + 2 \* Atan(1)|  
|逆正割 (Asec(x))|2 * Atan(1) – Atan(Sign(x)/Sqrt (x \* x 1))|  
|逆の余割 (Acsc(x))|Atan(Sign(x) / Sqrt(x * x – 1))|  
|逆余接 (Acot(x))|2 * Atan(1) - Atan(x)|  
|双曲線正弦 (Sinh(x))|(Exp(x) – Exp(-x)) / 2|  
|双曲線余弦 (Cosh(x))|(Exp(x) + Exp(-x)) / 2|  
|ハイパーボリック タンジェント (Tanh(x))|(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))|  
|双曲線正割 (Sech(x))|2 / (Exp(x) + Exp(-x))|  
|Hyperbolic cosecant (Csch(x))|2 / (Exp(x) – Exp(-x))|  
|双曲線余接 (Coth(x))|(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))|  
|逆双曲線正弦 (Asinh(x))|ログ (x + Sqrt (x * x + 1))|  
|逆双曲線余弦 (Acosh(x))|ログ (x + Sqrt (x * x 1))|  
|逆ハイパーボリック タンジェント (Atanh(x))|Log((1 + x) / (1 – x)) / 2|  
|逆双曲線正割 (AsecH(x))|Log ((Sqrt (-x * x + 1) + 1)/x)|  
|逆双曲線余割 (Acsch(x))|Log((Sign(x) * Sqrt (x \* x + 1) + 1)/x)|  
|逆双曲線余接 (Acoth(x))|Log((x + 1) / (x – 1)) / 2|  
  
## <a name="see-also"></a>関連項目

- [数値演算関数](../../../visual-basic/language-reference/functions/math-functions.md)
