---
title: アセンブリの内容
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- assemblies [.NET Core]
- single-file assemblies
- multifile assemblies [.NET Framework]
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
ms.openlocfilehash: 9ca12ee4bd993db3dd200a3b340c220ce5188796
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122533"
---
# <a name="assembly-contents"></a>アセンブリの内容
一般に、静的アセンブリは次の 4 つの要素から構成されます。

- アセンブリ メタデータを保持する[アセンブリ マニフェスト](manifest.md)。

- 型メタデータ。  

- 型を実装する MSIL (Microsoft Intermediate Language) コード。 コンパイラによって 1 つ以上のソース コード ファイルから生成されます。

- 一連のリソース。  

このうち必須なのはアセンブリ マニフェストだけですが、アセンブリになんらかの機能を与えるには、型またはリソースのいずれかが必要になります。

次の図では、これらの要素を 1 つの物理ファイルにグループ化したものが示されています。

![MyAssembly.dll という名前のシングルファイル アセンブリを示す図。](./media/contents/single-file-assembly.gif)

この例では、MyAssembly.dll に含まれるアセンブリ マニフェストに記述されているように、3 つのファイルがすべて 1 つのアセンブリに属しています。 ファイル システムにとっては、これらは 3 つの独立したファイルです。 Util.netmodule というファイルは、アセンブリ情報を含んでいないため、モジュールとしてコンパイルされています。 アセンブリの作成時に、アセンブリ マニフェストが MyAssembly.dll に追加され、その Util.netmodule および Graphic.bmp との関係が示されます。

ソース コードをデザインするときは、作成するアプリケーションの機能を 1 つのファイルにまとめるのか複数のファイルに分割するのか、分割する場合は機能をどのように分けるのかを明確に決める必要があります。 .NET Framework コードをデザインする場合も同様に、機能を 1 つのアセンブリにまとめるのか複数のアセンブリに分割するのか、分割する場合は機能をどのように分割するのかを決めておく必要があります。

## <a name="see-also"></a>関連項目

- [.NET のアセンブリ](index.md)
- [アセンブリ マニフェスト](manifest.md)
- [アセンブリのセキュリティに関する考慮事項](security-considerations.md)
