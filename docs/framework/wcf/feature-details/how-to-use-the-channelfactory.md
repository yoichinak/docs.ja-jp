---
title: '方法: ChannelFactory を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: 4bb2053fb50931756e79d5346a3f14d2acbe04f6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595311"
---
# <a name="how-to-use-the-channelfactory"></a>方法: ChannelFactory を使用する
<xref:System.ServiceModel.ChannelFactory%601> ジェネリック クラスは、複数チャネルの作成に使用できるチャネル ファクトリの作成を必要とする高度なシナリオで使用します。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>ChannelFactory クラスの作成方法と使用方法  
  
1. Windows Communication Foundation (WCF) サービスをビルドして実行します。 詳細については、「[サービスの設計と実装](../designing-and-implementing-services.md)」、「[サービスの構成](../configuring-services.md)」、および「[ホスティングサービス](../hosting-services.md)」を参照してください。  
  
2. [ServiceModel メタデータユーティリティツール (svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、クライアントのコントラクト (インターフェイス) を生成します。  
  
3. クライアント コード内で、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して複数のエンドポイント リスナーを作成します。  
  
## <a name="example"></a>例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
