---
title: '方法: データサービス参照の追加 (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790740"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a>方法: データサービス参照の追加 (WCF Data Services)

Visual Studio の **[サービス参照の追加]** ダイアログボックスを使用して、WCF Data Services への参照を追加できます。 参照をデータ サービスに追加すると、Visual Studio で開発したクライアント アプリケーションのデータ サービスに容易にアクセスできます。 この手順を完了すると、データ サービスから取得されたメタデータに基づいてデータ クラスが生成されます。 詳細については、「[データサービスクライアントライブラリの生成](generating-the-data-service-client-library-wcf-data-services.md)」を参照してください。

## <a name="add-a-data-service-reference"></a>データサービス参照の追加

1. (オプション) データ サービスがソリューションの一部ではなく、実行していない場合は、データ サービスを開始して、データ サービスの URI を記録します。

2. Visual Studio の**ソリューションエクスプローラー**で、クライアントプロジェクトを右クリックし、[**サービス参照**の**追加** > ] を選択します。

3. データサービスが現在のソリューションの一部である場合は、 **[探索]** をクリックします。

     \- または -

     **[アドレス]** テキストボックスに、データサービスのベース URL (など) `http://localhost:1234/Northwind.svc`を入力し、[実行] をクリックします。

4. **[OK]** を選択します。

     データサービスリソースにアクセスして操作できるデータクラスを含む新しいコードファイルがプロジェクトに追加されます。

## <a name="see-also"></a>関連項目

- [クイック スタート](quickstart-wcf-data-services.md)
