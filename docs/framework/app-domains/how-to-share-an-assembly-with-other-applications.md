---
title: '方法: アセンブリを他のアプリケーションと共有する'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b4c183c3fc0b04121be8bbc2db4027887cbc3132
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644292"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>方法: アセンブリを他のアプリケーションと共有する
アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。  

他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ (GAC)](gac.md) にアセンブリを置く必要があります。  
  
アセンブリを共有するには:
  
1. アセンブリを作成します。 詳しくは、「[アセンブリを作成する](../../standard/assembly/create.md)」をご覧ください。  
  
2. アセンブリに厳密な名前を割り当てます。 詳細については、[厳密な名前でアセンブリに署名する](../../standard/assembly/sign-strong-name.md)」を参照してください。  
  
3. アセンブリにバージョン情報を割り当てます。 詳細については、「[アセンブリのバージョン管理](../../standard/assembly/versioning.md)」を参照してください。  
  
4. グローバル アセンブリ キャッシュにアセンブリを追加します。 詳細については、[アセンブリをグローバル アセンブリ キャッシュにインストールする](install-assembly-into-gac.md)」を参照してください。  
  
5. 他のアプリケーションからアセンブリに含まれる型にアクセスします。 詳細については、[厳密な名前のアセンブリを参照する](../../standard/assembly/reference-strong-named.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../api/index.md)
- [プログラミングの概念 (Visual Basic)](../../../api/index.md)
- [アセンブリを使用したプログラム](../../standard/assembly/index.md)
