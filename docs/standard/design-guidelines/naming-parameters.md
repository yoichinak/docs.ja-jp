---
title: パラメーターに名前を付ける
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- parameters, names
- names [.NET Framework], parameters
ms.assetid: ca3c956e-725a-441b-b4e3-eab5d472f41c
author: KrzysztofCwalina
ms.openlocfilehash: 0e5b33839372e303b96bd6b84949f9a82da2f689
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026309"
---
# <a name="naming-parameters"></a>パラメーターに名前を付ける
はっきりした理由の読みやすさを超えるパラメーターは、そのビジュアル デ ザイン ツール Intellisense および参照機能クラスを提供するときにドキュメントでは、デザイナーで表示されるため、パラメーター名のガイドラインに従う重要です。  
  
 **✓ DO** パラメーター名の camel 表記を使用します。  
  
 **✓ DO** わかりやすいパラメーター名を使用します。  
  
 **✓ CONSIDER** パラメーターの型ではなく、パラメーターの意味に基づく名前を使用します。  
  
### <a name="naming-operator-overload-parameters"></a>演算子のオーバー ロードのパラメーターの名前を付ける  
 **✓ DO** 使用`left`と`right`のパラメーターに意味がない場合は、二項演算子のオーバー ロード パラメーター名にします。  
  
 **✓ DO** 使用`value`で単項演算子のオーバー ロード パラメーター名はパラメーターに意味がない場合。  
  
 **✓ CONSIDER** 演算子にわかりやすい名前オーバー ロードのパラメーターの場合は重要な価値が追加されます。  
  
 **X DO NOT** 使用の省略形または数値の添字演算子のオーバー ロードのパラメーターの名前。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [名前付けのガイドライン](../../../docs/standard/design-guidelines/naming-guidelines.md)
