---
title: '方法: アセンブリから型およびメンバーの情報を取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f9d01715a9635b276ca87d94082bb4d3820084e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138880"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a>方法: アセンブリから型およびメンバーの情報を取得する
<xref:System.Reflection> 名前空間には、アセンブリから情報を取得するための多くのメソッドがあります。 このセクションでは、これらのメソッドの 1 つを実行する例を示します。 詳細については、「[リフレクションの概要](../../../docs/framework/reflection-and-codedom/reflection.md)」を参照してください。  
  
 アセンブリから型およびメンバーの情報を取得する例を次に示します。  
  
## <a name="example"></a>例  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a>関連項目

- [アプリケーション ドメインを使用したプログラミング](./application-domains.md#programming-with-application-domains)
- [リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)
- [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)
