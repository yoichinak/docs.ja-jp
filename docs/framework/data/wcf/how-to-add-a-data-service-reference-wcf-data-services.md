---
title: '方法: データ サービス参照 (WCF Data Services) の追加します。'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765532"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>方法: データ サービス参照 (WCF Data Services) の追加します。

使用することができます、**サービス参照の追加**WCF Data Services への参照を追加する Visual Studio でダイアログ。 参照をデータ サービスに追加すると、Visual Studio で開発したクライアント アプリケーションのデータ サービスに容易にアクセスできます。 この手順を完了すると、データ サービスから取得されたメタデータに基づいてデータ クラスが生成されます。 詳細については、次を参照してください。[データ サービス クライアント ライブラリの生成](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)します。

## <a name="add-a-data-service-reference"></a>データ サービス参照を追加します。

1. (オプション) データ サービスがソリューションの一部ではなく、実行していない場合は、データ サービスを開始して、データ サービスの URI を記録します。

2. Visual Studio での**ソリューション エクスプ ローラー**、クライアント プロジェクトを右クリックし、**追加** > **サービス参照の**します。

3. データ サービスが現在のソリューションの一部である場合は、クリックして**Discover**します。

     - または -

     **アドレス**テキスト ボックスに、入力、データ サービスのベース URL など`http://localhost:1234/Northwind.svc`、 をクリックし、**移動**します。

4. **[OK]** を選択します。

     アクセスして、データ サービス リソースとやり取りするデータ クラスを含む新しいコード ファイルは、プロジェクトに追加されます。

## <a name="see-also"></a>関連項目

- [クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)