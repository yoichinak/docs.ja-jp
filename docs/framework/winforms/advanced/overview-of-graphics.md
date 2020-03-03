---
title: グラフィックスについて
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using managed interface
- graphics [Windows Forms], about graphics
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
ms.openlocfilehash: f0e2fd9dcf31e5fdce16b5a3b6fd21eab6eab66a
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505324"
---
# <a name="overview-of-graphics"></a>グラフィックスについて
GDI + は、Microsoft Windows オペレーティング システムのサブシステムを形成するアプリケーション プログラミング インターフェイス (API です)。 GDI + は画面およびプリンター情報を表示する責任を負います。 その名前からわかるように、GDI + は GDI、以前のバージョンの Windows に含まれているグラフィックス デバイス インターフェイスの後継です。  
  
## <a name="managed-class-interface"></a>マネージド クラスのインターフェイス  
 GDI + API は、マネージ コードとして配置されているクラスのセットを通じて公開されます。 この一連のクラスと呼ばれる、*マネージ クラスのインターフェイス*GDI + にします。 次の名前空間は、マネージド クラスのインターフェイスを構成します。  
  
- <xref:System.Drawing>  
  
- <xref:System.Drawing.Drawing2D>  
  
- <xref:System.Drawing.Imaging>  
  
- <xref:System.Drawing.Text>  
  
- <xref:System.Drawing.Printing>  
  
 GDI + などのグラフィックス デバイス インターフェイスを持つ特定のディスプレイ デバイスの詳細について心配することがなく、画面またはプリンターの情報を表示できます。 プログラマでは、GDI + クラスによって提供されるメソッドを呼び出します。 次に、これらのメソッドで、特定のデバイス ドライバーへの適切な呼び出しを実行します。 GDI +、グラフィックス ハードウェアからアプリケーションを隔離します。 この分離により、プログラマはデバイスに依存しないアプリケーションを作成することをお勧めします。  
  
## <a name="see-also"></a>関連項目

- [グラフィックスの概要](graphics-overview-windows-forms.md)
