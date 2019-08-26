---
title: 方法:アセンブリを他のアプリケーションと共有する (C#)
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 954db3fe139ff307386fc182dbf16c60ce86bd30
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595732"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>方法:アセンブリを他のアプリケーションと共有する (C#)
アセンブリはプライベートまたは共有にすることができます。既定では、ほとんどの単純なプログラムは、他のアプリケーションによって使われることを意図されていないので、プライベート アセンブリで構成されます。  
  
 他のアプリケーションとアセンブリを共有するには、[グローバル アセンブリ キャッシュ](../../../../framework/app-domains/gac.md) (GAC) にアセンブリを置く必要があります。  
  
### <a name="sharing-an-assembly"></a>アセンブリの共有  
  
1. アセンブリを作成します。 詳しくは、「[アセンブリの作成](../../../../framework/app-domains/create-assemblies.md)」をご覧ください。  
  
2. アセンブリに厳密な名前を割り当てます。 詳細については、[方法:厳密な名前でアセンブリに署名する](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」を参照してください。  
  
3. アセンブリにバージョン情報を割り当てます。 詳細については、「[アセンブリのバージョン管理](../../../../framework/app-domains/assembly-versioning.md)」を参照してください。  
  
4. グローバル アセンブリ キャッシュにアセンブリを追加します。 詳細については、[方法:アセンブリをグローバル アセンブリ キャッシュにインストールする](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md)」を参照してください。  
  
5. 他のアプリケーションからアセンブリに含まれる型にアクセスします。 詳細については、[方法:厳密な名前のアセンブリを参照する](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../index.md)
- [アセンブリを使用したプログラミング](../../../../framework/app-domains/programming-with-assemblies.md)
