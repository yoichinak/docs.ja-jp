---
title: Windows コンテナーを展開しない状況
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを近代化 |Windows コンテナーをデプロイすべきでない場合
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 75db31a8f4599e9681c2c4156d93db5416d2ca96
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200741"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows コンテナーを展開しない状況

Windows コンテナーでは、一部の Windows テクノロジはサポートされていません。 その場合、引き続き Windows と IIS だけでは、通常、標準の Vm に移行する必要があります。

2018 年 5 月の時点での Windows コンテナーではサポートされていない場合: 

-   現在 Microsoft メッセージ キュー (MSMQ) は他の以前のリリースではなく Windows Server v1803 のリリースに基づく Windows コンテナーで使用可能なではのみです。 

    -   [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [ディスカッション フォーラム](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft 分散トランザクション コーディネーター (MSDTC) は、現在、Windows コンテナーではサポートされません。

    -   [GitHub の問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Microsoft Office は、現在のコンテナーをサポートしていません。

    -   [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   アプリの UI (ビジュアルなユーザー インターフェイスでクライアント アプリケーション) はサポートされているシナリオではありません。

-   Windows インフラストラクチャの役割 (DNS、DHCP、DC、NTP、印刷、ファイル サーバー、IAM など) はサポートされるシナリオではありません。

その他のサポートされていないシナリオと、コミュニティからの要求は、Windows コンテナーの UserVoice フォーラムを参照してください:<https://windowsserver.uservoice.com/forums/304624-containers>します。

### <a name="additional-resources"></a>その他の技術情報

-   **仮想マシンと Azure でのコンテナー**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
>[前へ](deploy-existing-net-apps-as-windows-containers.md)
>[次へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)