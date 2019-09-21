---
title: '方法: アセンブリを読み込み、アンロードする'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: 77ea97c2fc324287e9c697d630def98241432c9f
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972673"
---
# <a name="how-to-load-and-unload-assemblies"></a>方法: アセンブリを読み込み、アンロードする
プログラムから参照されるアセンブリは、共通言語ランタイムによって自動的に読み込まれますが、特定のアセンブリを現在のアプリケーション ドメインに動的に読み込むこともできます。 詳細については、「[方法 :アプリケーション ドメインにアセンブリを読み込む](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。

.NET Framework では、アセンブリが含まれるすべてのアプリケーション ドメインをアンロードせずに、個々のアセンブリをアンロードする方法はありません。 アセンブリがスコープの外にある場合であっても、実際のアセンブリ ファイルは、これらのアセンブリ ファイルを含むすべてのアプリケーション ドメインがアンロードされるまでは読み込まれたままになります。 .Net Core では、<xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> クラスによってアセンブリのアンロードが処理されます。 詳細については、「[.NET Core でアセンブリのアンローダビリティを使用およびデバッグする方法](unloadability.md)」を参照してください。

## <a name="load-and-unload-assemblies"></a>アセンブリを読み込み、アンロードする

アセンブリをアプリケーション ドメインに読み込むには、<xref:System.AppDomain> クラスと <xref:System.Reflection.Assembly> クラスに含まれるいくつかの読み込みメソッドのいずれかを使用します。 詳細については、「[方法 :アプリケーション ドメインにアセンブリを読み込む](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)」を参照してください。 .NET Core でサポートされるアプリケーション ドメインは 1 つだけであることに注意してください。 

.NET Framework でアセンブリをアンロードするには、アセンブリを含まれるすべてのアプリケーション ドメインをアンロードする必要があります。 アプリケーション ドメインをアンロードするには、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドを使用します。 詳細については、「[方法 :アプリケーション ドメインをアンロードする](../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。

.NET Framework アプリケーションで、一部のアセンブリだけをアンロードする場合は、新しいアプリケーション ドメインを作成し、そのドメイン内でコードを実行した後、そのアプリケーション ドメインをアンロードします。 詳細については、「[方法 :アプリケーション ドメインをアンロードする](../../framework/app-domains/how-to-unload-an-application-domain.md)」を参照してください。  

## <a name="see-also"></a>関連項目

- [C# プログラミング ガイド](../../csharp/programming-guide/index.md)
- [プログラミングの概念 (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [.NET のアセンブリ](index.md)
- [方法: アプリケーション ドメインにアセンブリを読み込む](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
