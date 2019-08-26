---
title: 方法:アセンブリを読み込み、アンロードする (C#)
ms.date: 07/20/2015
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 3f3c244a74e029eeaead77f561cd4c1adfca519a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/19/2019
ms.locfileid: "69595841"
---
# <a name="how-to-load-and-unload-assemblies-c"></a>方法:アセンブリを読み込み、アンロードする (C#)
プログラムから参照されるアセンブリは、ビルド時に自動的に読み込まれますが、実行時に特定のアセンブリを現在のアプリケーション ドメインに読み込むこともできます。 詳細については、[方法:アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」をご覧ください。  
  
 個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。  
  
 一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成して、そのドメイン内でコードを実行した後で、そのアプリケーション ドメインをアンロードしてください。 詳細については、[方法:アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」をご覧ください。  
  
### <a name="to-load-an-assembly-into-an-application-domain"></a>アセンブリをアプリケーション ドメインに読み込むには  
  
1. <xref:System.AppDomain> クラスと <xref:System.Reflection> クラスに含まれるいくつかの load メソッドの 1 つを使用します。 詳細については、[方法:アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」をご覧ください。  
  
### <a name="to-unload-an-application-domain"></a>アプリケーション ドメインをアンロードするには  
  
1. 個々のアセンブリをアンロードするには、アセンブリを含むすべてのアプリケーション ドメインを必ずアンロードする必要があります。 `Unload` の <xref:System.AppDomain> メソッドを使用してアプリケーション ドメインをアンロードします。 詳細については、[方法:アプリケーション ドメインをアンロードする](../../../../framework/app-domains/how-to-unload-an-application-domain.md)」をご覧ください。  
  
## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../index.md)
- [.NET のアセンブリ](../../../../standard/assembly/index.md)
- [方法: アプリケーション ドメインにアセンブリを読み込む](../../../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
