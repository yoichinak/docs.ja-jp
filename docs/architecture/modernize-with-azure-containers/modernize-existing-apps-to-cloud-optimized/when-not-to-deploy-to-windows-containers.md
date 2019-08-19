---
title: Windows コンテナーを展開しない状況
description: Azure クラウドおよび Windows コンテナーで既存の .NET アプリケーションを最新化する |Windows コンテナーに展開しない場合
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577955"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Windows コンテナーを展開しない状況

一部の Windows テクノロジは、Windows コンテナーではサポートされていません。 そのような場合でも、通常は Windows と IIS だけを使用して標準 Vm に移行する必要があります。

Windows コンテナーでサポートされていないケース (2018 年5月):

- Microsoft Message Queuing (MSMQ) は、現在、Windows Server v1803 リリースに基づく Windows コンテナーでのみ使用できますが、それ以外の以前のリリースでは使用できません。

  - [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [ディスカッションフォーラム](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft 分散トランザクションコーディネーター (MSDTC) は、現在、Windows コンテナーではサポートされていません。

  - [GitHub の問題](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Microsoft Office は現在、コンテナーをサポートしていません。

  - [UserVoice 要求フォーラム](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- UI アプリ (ビジュアルユーザーインターフェイスを使用したクライアントアプリ) は、サポートされていないシナリオです。

- Windows インフラストラクチャの役割 (DNS、DHCP、DC、NTP、印刷、ファイルサーバー、IAM など) は、サポートされていないシナリオです。

コミュニティからのサポートされていないその他のシナリオと要求については、 <https://windowsserver.uservoice.com/forums/304624-containers>「Windows コンテナーの UserVoice フォーラム:」を参照してください。

### <a name="additional-resources"></a>その他の技術情報

- **Azure の仮想マシンとコンテナー**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [前へ](deploy-existing-net-apps-as-windows-containers.md)
> [次へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
