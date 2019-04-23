---
title: '方法: MMC スナップインで証明書の表示'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59167506"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>方法: MMC スナップインで証明書の表示
使用することができますをセキュリティで保護されたクライアントまたはサービスを作成するときに、[証明書](working-with-certificates.md)資格情報として。 たとえば、資格情報の一般的な種類は、X.509 証明書を作成する、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType>メソッド。 

Windows システムで Microsoft 管理コンソール (MMC) とを確認する証明書ストアの 3 つの異なる種類があります。

- ローカル コンピューターの場合:ストアは、デバイスのローカルと、デバイス上のすべてのユーザーにグローバルです。

- 現在のユーザー:ストアでは、デバイス上の現在のユーザー アカウントにローカルです。

- サービス アカウント:ストアでは、デバイスの特定のサービスにローカルです。

## <a name="view-certificates-in-the-mmc-snap-in"></a>MMC スナップインで証明書の表示 

次の手順では、適切な証明書を検索するローカル デバイス上のストアを確認する方法を示しています。 
  
1. 選択**実行**から、**開始**] メニューの [し、入力*mmc*します。 

    MMC が表示されます。 
  
2. **ファイル**メニューの **スナップインの追加/削除**します。 
    
    **スナップインを追加または**ウィンドウが表示されます。
  
3. **利用できるスナップイン**一覧で、選択**証明書**を選択し、**追加**します。  

    ![証明書スナップインの追加します。](./media/mmc-add-certificate-snap-in.png)
  
4. **証明書スナップイン**ウィンドウで、**コンピューター アカウント**、し、**次**します。 
  
    必要に応じて、選択**ユーザー アカウント**、現在のユーザーまたは**サービス アカウント**特定のサービスです。 

    > [!NOTE]
    > ない場合、管理者のデバイス、ユーザー アカウントに対してのみ証明書を管理できます。
  
5. **コンピューターの選択**] ウィンドウのままに**ローカル コンピューター**を選択し、[**完了**します。  
  
6. **スナップインの追加または削除**ウィンドウで、 **OK**します。  
  
    ![証明書スナップインの追加します。](./media/mmc-certificate-snap-in-selected.png)

7. 省略可能:**ファイル**メニューの **保存**または**名前を付けて保存**後で使用できる MMC コンソール ファイルを保存します。  

8. MMC スナップインで証明書を表示する選択**コンソール ルート**左側のウィンドウでを展開し、**証明書 (ローカル コンピューター)** します。

    証明書の種類ごとのディレクトリの一覧が表示されます。 各証明書のディレクトリからすることができますを表示、エクスポート、インポート、およびその証明書を削除します。

## <a name="view-certificates-with-the-certificate-manager-tool"></a>証明書マネージャー ツールを使用して証明書の表示

ことができますも表示、エクスポート、インポート、および証明書マネージャー ツールを使用して証明書を削除します。

### <a name="to-view-certificates-for-the-local-device"></a>ローカルのデバイス用の証明書を表示するには

1. 選択**実行**から、**開始**] メニューの [し、入力*certlm.msc*します。 

    ローカルのデバイスの証明書マネージャー ツールが表示されます。 
  
2. 下に、証明書を表示する**証明書 - ローカル コンピューター**左側のウィンドウで表示する証明書の種類のディレクトリを展開します。

### <a name="to-view-certificates-for-the-current-user"></a>現在のユーザーの証明書を表示するには

1. 選択**実行**から、**開始**] メニューの [し、入力*certmgr.msc*します。 

    現在のユーザーの証明書マネージャー ツールが表示されます。 
  
2. 下に、証明書を表示する**証明書 - 現在のユーザー**左側のウィンドウで表示する証明書の種類のディレクトリを展開します。

## <a name="see-also"></a>関連項目

- [証明書の使用](working-with-certificates.md)
- [方法: 開発中に使用するための一時的な証明書を作成します。](how-to-create-temporary-certificates-for-use-during-development.md)
- [方法: 証明書のサムプリントを取得します。](how-to-retrieve-the-thumbprint-of-a-certificate.md)
