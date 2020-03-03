---
title: '方法: アセンブリを他のアプリケーションと共有する'
ms.date: 08/19/2019
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: b1ef195458dd2de95eeb5e25089339e55d9e3fbb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972883"
---
# <a name="how-to-share-an-assembly-with-other-applications"></a>方法: アセンブリを他のアプリケーションと共有する
アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。  

他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ (GAC)](gac.md) にアセンブリを置く必要があります。  
  
アセンブリを共有するには:
  
1. アセンブリを作成します。 詳しくは、「[アセンブリを作成する](../../standard/assembly/create.md)」をご覧ください。  
  
2. アセンブリに厳密な名前を割り当てます。 詳細については、「[方法 :厳密な名前でアセンブリに署名する](../../standard/assembly/sign-strong-name.md)」を参照してください。  
  
3. アセンブリにバージョン情報を割り当てます。 詳細については、「[アセンブリのバージョン管理](../../standard/assembly/versioning.md)」を参照してください。  
  
4. グローバル アセンブリ キャッシュにアセンブリを追加します。 詳細については、「[方法 :アセンブリをグローバル アセンブリ キャッシュにインストールする](install-assembly-into-gac.md)」を参照してください。  
  
5. 他のアプリケーションからアセンブリに含まれる型にアクセスします。 詳細については、「[方法 :厳密な名前のアセンブリを参照する](../../standard/assembly/reference-strong-named.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../../api/index.md)
- [プログラミングの概念 (Visual Basic)](../../../api/index.md)
- [アセンブリを使用したプログラム](../../standard/assembly/program.md)
