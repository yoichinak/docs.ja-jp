---
title: UriTemplate テーブル ディスパッチャーのサンプル
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143682"
---
# <a name="uritemplate-table-dispatcher-sample"></a>UriTemplate テーブル ディスパッチャーのサンプル
<xref:System.UriTemplateTable> クラスには、<xref:System.UriTemplate> インスタンスのセットを使用するための、ディクショナリに似た結合テーブル構造が用意されています。 このサンプルでは、`UriTemplateTable` クラスの一般的な使用シナリオとして、`UriTemplateTable` を使用してビルドされた基本的なディスパッチ エンジンを示します。  
  
 このサンプルでは、次の `UriTemplateTable` クラスに関連する重要な概念を示します。  
  
- `UriTemplates` の `UriTemplateTable` とのデリゲートの関連付け。  
  
- <xref:System.UriTemplateTable.MatchSingle%2A> を使用した特定の URI の正しいハンドラ デリゲートの取得。  
  
- 要求を処理するためのハンドラー デリゲートの呼び出し。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
2. 単一または複数のコンピューターにまたがる構成でサンプルを実行するには[、「Windows コミュニケーション ファウンデーション サンプルの実行」の手順に](../../../../docs/framework/wcf/samples/running-the-samples.md)従います。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> このディレクトリが存在しない場合は[、.NET Framework 4 の Windows コミュニケーション ファウンデーション (WCF) および Windows ワークフローファウンデーション (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)に移動して、すべての Windows 通信基盤 (WCF) とサンプルを[!INCLUDE[wf1](../../../../includes/wf1-md.md)]ダウンロードします。 このサンプルは、次のディレクトリに格納されます。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a>関連項目

- [UriTemplate テーブル](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [ウリテンプレート](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
