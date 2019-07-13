---
title: '方法: Probe 要求の探索バージョンを特定する'
ms.date: 03/30/2017
ms.assetid: b3c4e2e2-2957-4074-ae6a-776a5ca84278
ms.openlocfilehash: 8fbc3936278a5c6f403f48b59390c69c64378004
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425269"
---
# <a name="how-todetermine-the-discovery-version-of-a-probe-request"></a>方法: Probe 要求の探索バージョンを特定する

探索プロキシでは、異なる探索バージョンを使用する複数の探索エンドポイントを公開する場合があります。 ときに、UDP マルチキャスト Probe 要求を受け取った、プロキシにプロキシがマルチキャスト抑制メッセージで応答する必要があります。 これを行うには、要求の探索バージョンを把握することになります。

## <a name="to-determine-the-discovery-version-of-a-probe-request"></a>Probe 要求の探索バージョンを特定するには

プローブ要求に応答するメソッドで (たとえば<xref:System.ServiceModel.Discovery.DiscoveryProxy.OnBeginFind%2A?displayProperty=nameWithType>)、静的なを使用して、<xref:System.ServiceModel.OperationContext.Current%2A?displayProperty=nameWithType>検索対象のプロパティを<xref:System.ServiceModel.Discovery.DiscoveryOperationContextExtension>次のコードに示すように、します。

```csharp
DiscoveryOperationContextExtension doce = OperationContext.Current.Extensions.Find<DiscoveryOperationContextExtension>();
// Access the discovery version from the DiscoveryOperationContextExtension
doce.DiscoveryVersion;
```

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion%2A>
- [探索プロキシの実装](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)
