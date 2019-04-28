---
title: シールされていないクラス
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- classes [.NET Framework], unsealed
- unsealed classes
- inheritance, classes
ms.assetid: 9a3bd505-90f5-4053-9f0d-3cf5fa3d3ebf
author: KrzysztofCwalina
ms.openlocfilehash: d7174de7ddf062b829672e04952c1010fcb74058
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61778795"
---
# <a name="unsealed-classes"></a>シールされていないクラス
シール クラスから継承することはできませんし、機能拡張は、します。 これに対し、封印されていないクラスから継承できるクラスと呼びます。  
  
 **✓ CONSIDER** 安価なを提供するのにまだ高く評価されたフレームワークを拡張機能として、仮想またはプロテクト メンバーを追加なしで封印されていないクラスを使用します。  
  
 多くの場合、開発者はカスタム コンス トラクター、新しいメソッドは、メソッドのオーバー ロードなどの便利なメンバーを追加するための封印されていないクラスから継承したいと考えているとします。 たとえば、`System.Messaging.MessageQueue`が封印されていないと、できるので、ユーザーがその既定値を特定のキューのパスにカスタムのキューを作成する特定のシナリオ用の API を簡略化するカスタム メソッドを追加します。  
  
 既定ではほとんどのプログラミング言語でクラスが封印されていないし、これは、推奨された既定のフレームワークのほとんどのクラスにもします。 封印されていない型によって提供される拡張機能は、フレームワークのユーザーによって非常にありがたいと封印されていない型に関連付けられている相対的に低いテスト コストのために提供する非常に低コストです。  
  
 *Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*  
  
 *Pearson Education, Inc. からのアクセス許可によって了承を得て転載[Framework デザイン ガイドライン。規則、手法、および再利用可能な .NET ライブラリの第 2 版のパターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina、Brad 内容では、Microsoft Windows の開発シリーズの一部として、Addison-wesley Professional、2008 年 10 月 22日を公開します。*  
  
## <a name="see-also"></a>関連項目

- [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)
- [機能拡張のデザイン](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
- [シール](../../../docs/standard/design-guidelines/sealing.md)
