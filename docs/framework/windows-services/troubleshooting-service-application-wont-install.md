---
title: トラブルシューティング:サービス アプリケーションをインストールできない場合
ms.date: 03/30/2017
helpviewer_keywords:
- troubleshooting service applications
- services, troubleshooting
- services, debugging
- Windows NT services, troubleshooting
- troubleshooting NT services
- Windows Service applications, troubleshooting
ms.assetid: 45c48e2e-b97d-44bc-8896-14f328e0ce33
author: ghogen
ms.openlocfilehash: d04a0ddcef9ff7c31abd422f7f9fba34e804d2b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935413"
---
# <a name="troubleshooting-service-application-wont-install"></a>トラブルシューティング:サービス アプリケーションをインストールできない場合
サービス アプリケーションが正しくインストールされない場合は、サービス クラスの <xref:System.ServiceProcess.ServiceBase.ServiceName%2A> プロパティが、そのサービスのインストーラーで示されているのと同じ値に設定されていることを確認します。 サービスが正しくインストールされるためには、両方のインスタンスで同じ値になっている必要があります。  
  
> [!NOTE]
> また、インストール ログを見て、インストール プロセスについてのフィードバックを確認することもできます。  
  
 同じ名前の別のサービスが既にインストールされているかどうかも確認する必要があります。 インストールが成功するには、サービス名が一意である必要があります。  
  
## <a name="see-also"></a>関連項目

- [Windows サービス アプリケーションの概要](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)
