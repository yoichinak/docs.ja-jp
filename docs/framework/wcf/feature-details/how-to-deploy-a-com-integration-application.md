---
title: '方法: COM+ 統合アプリケーションを展開する'
ms.date: 03/30/2017
ms.assetid: 2e5a0510-db3c-4988-a09c-696285836650
ms.openlocfilehash: fcf525943e6e453253c6f4d3bcfa8a1a08df6909
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343380"
---
# <a name="how-to-deploy-a-com-integration-application"></a>方法: COM+ 統合アプリケーションを展開する
COM+ 統合アプリケーションを作成した後、これを別のコンピューターに展開する必要が生じる場合があります。 ここでは、COM+ 統合アプリケーションをコンピューター間で移動する方法を説明します。  
  
### <a name="moving-a-com-hosted-integration-app"></a>COM+ ホスト統合アプリケーションの移動  
  
1. WCF が両方のコンピューターにインストールされていることを確認します。  
  
2. コンピューター A からアプリケーションをエクスポートします。  
  
3. コンピューター B にアプリケーションをインポートします。  
  
4. アプリケーション ルート ディレクトリを設定します。 通常これは %PROGRAMFILES%/ComPlus Applications/{AppGUID} になります。  
  
5. コンピューター A のアプリケーション ルート ディレクトリにある Application.config ファイルおよび Application.manifest ファイルを、コンピューター B のアプリケーション ルート ディレクトリにコピーします。  
  
6. コンピューター B の Application.config ファイルのサービス エンドポイント アドレスを編集して、コンピューター B が識別されるようにします。 たとえば、`http://machineA/MyService` を `http://machineB/MyService` に変更します。  
  
### <a name="moving-a-web-hosted-integration-application"></a>Web ホスト統合アプリケーションの移動  
  
1. WCF が両方のコンピューターにインストールされていることを確認します。  
  
2. コンピューター A からアプリケーションをエクスポートします。  
  
3. コンピューター B にアプリケーションをインポートします。  
  
4. コンピューター B で IIS vroot を作成します。  
  
5. コンピューター A の vroot にある .svc ファイル (componentName.svc) と Web.config ファイルを、コンピューター B で新しく作成した vroot にコピーします。  
  
## <a name="see-also"></a>関連項目

- [COM+ アプリケーションとの統合の概要](../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications-overview.md)
- [方法: COM + サービス設定を構成します。](../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
- [方法: COM + サービス モデル構成ツールを使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
