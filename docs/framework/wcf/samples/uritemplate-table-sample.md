---
title: UriTemplate テーブル サンプル
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: 9d60de39c8c025b31c45c79309442906fc3aab4e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044568"
---
# <a name="uritemplate-table-sample"></a>UriTemplate テーブル サンプル
<xref:System.UriTemplateTable> クラスには、`UriTemplate` インスタンスのセットを使用するための、ディクショナリに似た結合テーブル構造が用意されています。 特定の URI (Uniform Resource Identifier) をテーブル内のすべてのテンプレートと効率よく照合でき、照合されたテンプレートに関連付けられたデータを取得できます。  
  
 このサンプルでは、次の `UriTemplateTable` クラスに関連する重要な概念を示します。  
  
- `UriTemplateTable` をインスタンス化する構文  
  
- `UriTemplateTable` へのキー/値ペアのセットの追加  
  
- <xref:System.UriTemplateTable.MatchSingle%2A> を使用した候補 URI とテーブルの照合  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
2. サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a>関連項目

- [UriTemplate テーブル ディスパッチャー](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [UriTemplate](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
