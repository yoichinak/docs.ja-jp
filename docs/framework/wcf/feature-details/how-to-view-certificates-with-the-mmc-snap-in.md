---
title: '方法: MMC スナップインを使用して証明書を表示する'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184777"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>方法: MMC スナップインを使用して証明書を表示する
セキュリティで保護されたクライアントまたはサービスを作成する場合、[証明書](working-with-certificates.md)を資格情報として使用できます。 たとえば、一般的な資格情報の種類は、メソッドで作成する X.509 証明書<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>です。

Windows システムの Microsoft 管理コンソール (MMC) で調べることができる証明書ストアには、次の 3 種類があります。

- ローカル コンピューター: ストアはデバイスに対してローカルで、デバイス上のすべてのユーザーにグローバルです。

- 現在のユーザー: ストアは、デバイス上の現在のユーザー アカウントにローカルです。

- サービス アカウント: ストアは、デバイス上の特定のサービスに対してローカルです。

## <a name="view-certificates-in-the-mmc-snap-in"></a>MMC スナップインで証明書を表示する

次の手順では、ローカル デバイス上のストアを調べて、適切な証明書を見つける方法を示します。
  
1. **[スタート]** メニューから [ファイル名を**指定して実行**] を選択し、「 *mmc*」と入力します。

    MMC が表示されます。
  
2. [**ファイル]** メニューの [**スナップインの追加と削除**] をクリックします。

    [**スナップインの追加と削除**] ウィンドウが表示されます。
  
3. [**利用できるスナップイン**] ボックスの一覧で [**証明書**] を選択し、[**追加**] を選択します。  

    ![証明書スナップインの追加](./media/mmc-add-certificate-snap-in.png)
  
4. [**証明書スナップイン**] ウィンドウで、[コンピュータ**アカウント**] を選択し、[**次へ**] を選択します。
  
    必要に応じて、現在**のユーザーに対して [ユーザー アカウント**] を選択するか、特定のサービスの**サービス アカウント**を選択します。

    > [!NOTE]
    > デバイスの管理者でない場合は、自分のユーザー アカウントの証明書のみを管理できます。
  
5. [**コンピュータの選択]** ウィンドウで、[**ローカル コンピュータ**] を選択したまま、[**完了**] を選択します。  
  
6. [**スナップインの追加と削除**] ウィンドウで **、[OK] を**選択します。  
  
    ![証明書スナップインの追加](./media/mmc-certificate-snap-in-selected.png)

7. オプション: 「**ファイル」** メニューで、「**保存**」または「**名前を付けて保存**」を選択して、後で使用するために MMC コンソール・ファイルを保存します。  

8. MMC スナップインで証明書を表示するには、左側のウィンドウで **[コンソール ルート**] を選択し、[**証明書 (ローカル コンピュータ)]** を展開します。

    各種類の証明書のディレクトリの一覧が表示されます。 各証明書ディレクトリから、証明書の表示、エクスポート、インポート、および削除を行うことができます。

## <a name="view-certificates-with-the-certificate-manager-tool"></a>証明書マネージャ ツールを使用して証明書を表示する

証明書マネージャ ツールを使用して、証明書の表示、エクスポート、インポート、および削除を行うこともできます。

### <a name="to-view-certificates-for-the-local-device"></a>ローカル デバイスの証明書を表示するには

1. **[スタート]** メニューから [ファイル名を**指定して実行**] をクリックし *、「certlm.msc」* と入力します。

    ローカル デバイスの証明書マネージャ ツールが表示されます。
  
2. 証明書を表示するには、左側のウィンドウの [**証明書 - ローカル コンピューター** ] で、表示する証明書の種類のディレクトリを展開します。

### <a name="to-view-certificates-for-the-current-user"></a>現在のユーザーの証明書を表示するには

1. **[スタート]** メニューから [ファイル名を**指定して実行**] をクリックし *、certmgr.msc*と入力します。

    現在のユーザーの証明書マネージャ ツールが表示されます。
  
2. 証明書を表示するには、左側のウィンドウの [**証明書 - 現在のユーザー** ] の下で、表示する証明書の種類のディレクトリを展開します。

## <a name="see-also"></a>関連項目

- [証明書の操作](working-with-certificates.md)
- [方法: 開発中に使用する一時的な証明書を作成する](how-to-create-temporary-certificates-for-use-during-development.md)
- [方法: 証明書の拇印を取得する](how-to-retrieve-the-thumbprint-of-a-certificate.md)
