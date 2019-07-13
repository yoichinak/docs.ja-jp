---
title: '方法: ローカライズ可能アプリケーションでリソースを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- applications [WPF], localizable
- localizable applications [WPF]
ms.assetid: 08539ad6-7fca-4f34-b82b-ff439e11dfa7
ms.openlocfilehash: ad257e7703bcee8f71da78ad5928d7999365c38f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57376163"
---
# <a name="how-to-use-resources-in-localizable-applications"></a>方法: ローカライズ可能アプリケーションでリソースを使用する
ローカライズを調整すること、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]を異なるカルチャにします。 そのためには、タイトル、キャプション、リスト ボックス項目などのテキストを翻訳する必要があります。 翻訳しやすいように、翻訳される項目はリソース ファイルにまとめられています。 参照してください[アプリケーションをローカライズする](how-to-localize-an-application.md)ローカリゼーション用リソース ファイルを作成する方法についてはします。 させる、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションをローカライズ可能で、開発者がローカライズ可能なすべてのリソースをリソース アセンブリにビルドする必要があります。 さまざまな言語にローカライズされたリソース アセンブリと分離コードは リソース管理を使用して[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)]を読み込めません。 必要なファイルのいずれかを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションは、プロジェクト ファイル (.proj) です。 アプリケーションで使用するすべてのリソースをプロジェクト ファイルに含める必要があります。 このコード例を次に示します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]  
  
 `<Resource Include="data\picture1.jpg"/>`  
  
 `<EmbeddedResource Include="data\stringtable.en-US.restext"/>`  
  
 インスタンス化する、アプリケーションで、リソースを使用する<xref:System.Resources.ResourceManager>を使用するリソースを読み込むとします。 その方法を次に示します。  
  
 [!code-csharp[LocalizationResources#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationResources/CSharp/page1.xaml.cs#2)]
