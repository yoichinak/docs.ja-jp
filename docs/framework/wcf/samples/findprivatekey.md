---
title: FindPrivateKey サンプルの WCF
ms.date: 12/04/2017
helpviewer_keywords:
- FindPrivateKey
ms.assetid: 16b54116-0ceb-4413-af0c-753bb2a785a6
ms.openlocfilehash: b89d135d7412f10cb9de1e4bda1aaab14b29cbf0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490772"
---
# <a name="findprivatekey-sample"></a>FindPrivateKey サンプル

証明書ストア内の特定の X.509 証明書に関連付けられている秘密キー ファイルの場所と名前を見つけることが困難な場合があります。 FindPrivateKey.exe ツールを使用すると、この処理を容易に実行できます。

> [!IMPORTANT]
> FindPrivateKey は、使用する前にコンパイルする必要があるサンプルです。 参照してください、 [FindPrivateKey プロジェクトをビルドする](#to-build-the-findprivatekey-project)FindPrivateKey ツールをビルドする方法についてのセクション。

X.509 証明書は、コンピューターの管理者または任意のユーザーによってインストールされます。 ただし、証明書は、別のアカウントで実行されているサービスによってアクセスできます。 たとえば、ネットワーク サービス アカウント。

別のアカウントでは、秘密キー ファイルへアクセスできない場合があります。これは、証明書が最初にこのアカウントによってインストールされていないからです。 FindPrivateKey ツールでは、指定された X.509 証明書の秘密キー ファイルの場所を検索できます。 特定の X.509 証明書の秘密キー ファイルの場所がわかれば、このファイルに対するアクセス許可の追加または削除を実行できます。

セキュリティ証明書を使用するサンプルの FindPrivateKey ツールを使用して、 *Setup.bat*ファイル。 秘密キー ファイルが見つかったら、その他のツールをなど、使用できる*Cacls.exe*ファイルに適切なアクセス権を設定します。

自己ホスト型の実行可能ファイルなどのユーザー アカウントで Windows Communication Foundation (WCF) サービスを実行している場合は、ユーザー アカウントがファイルに読み取り専用アクセスを持つことを確認します。 WCF サービスでは、インターネット インフォメーション サービス (IIS) を実行するときに、サービスが実行する既定のアカウントは IIS 7 と以前のバージョンで、ネットワーク サービスまたは IIS 7.5、およびそれ以降のバージョンのアプリケーション プール Id です。 詳細については、次を参照してください。[アプリケーション プール Id](/iis/manage/configuring-security/application-pool-identities)します。

## <a name="examples"></a>使用例

対象のプロセスは読み取り権限がない証明書にアクセスするときに次の例のような例外メッセージを参照してください。

```
System.ArgumentException was unhandled
Message="The certificate 'CN=localhost' must have a private key that is capable of key exchange.  The process must have access rights for the private key."
Source="System.ServiceModel"
```

これが発生して FindPrivateKey ツールを使用して、秘密キー ファイルを検索し、サービスが実行されているプロセスの右へのアクセスを設定します。 たとえば、これは行えます Cacls.exe ツールを使用して次の例に示すように。

```
cacls.exe "C:\Documents and Settings\All Users\Application Data\Microsoft\Crypto\RSA\MachineKeys\8aeda5eb81555f14f8f9960745b5a40d_38f7de48-5ee9-452d-8a5a-92789d7110b1" /E /G "NETWORK SERVICE":R
```

#### <a name="to-build-the-findprivatekey-project"></a>FindPrivateKey プロジェクトをビルドするには

プロジェクトをダウンロードするには、次を参照してください。 [Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://www.microsoft.com/download/details.aspx?id=21459)します。

1. ファイル エクスプ ローラーを開きに移動、 *WF_WCF_Samples\WCF\Setup\FindPrivateKey\CS*サンプルがインストールされているディレクトリの場所の下のフォルダー。

2. .sln ファイルのアイコンをダブルクリックして、このファイルを Visual Studio で開きます。

3. **ビルド**メニューの **ソリューションのリビルド**します。

4. ソリューションをビルドするには、ファイルが生成されます。FindPrivateKey.exe します。

## <a name="conventionscommand-line-entries"></a>規則-コマンドラインのエントリ

 "[*オプション*]"は省略可能なパラメーターのセットを表します。

 "{*オプション*}"は必須パラメーターのセットを表します。

 "*option1* &#124; *option2*"オプションのセットから選択を表します。

 "\<*値*>"を入力するパラメーター値を表します。

## <a name="usage"></a>使用法

```
FindPrivateKey <storeName> <storeLocation> [{ {-n <subjectName>} | {-t <thumbprint>} } [-f | -d | -a]]
```

この場合、

```
       <subjectName> The subject name of the certificate
       <thumbprint>  The thumbprint of the certificate (You can use the Certmgr.exe tool to find this)
       -f            output file name only
       -d            output directory only
       -a            output absolute file name
```

コマンド プロンプト パラメーターが指定されていない場合は、このヘルプ テキストが表示されます。

## <a name="examples"></a>使用例

この例のサブジェクト名を持つ証明書のファイル名を検索する"CN = localhost"、現在のユーザーの個人用ストアにします。

```
FindPrivateKey My CurrentUser -n "CN=localhost"
```

この例のサブジェクト名を持つ証明書のファイル名を検索する"CN = localhost"、個人用の出力ディレクトリの完全なパスと、現在のユーザーのストアします。

```
FindPrivateKey My CurrentUser -n "CN=localhost" -a
```

この例では、ローカル コンピューターの Personal ストアで、"03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52" というサムプリントを持つ証明書のファイル名を検索します。

```
FindPrivateKey My LocalMachine -t "03 33 98 63 d0 47 e7 48 71 33 62 64 76 5c 4c 9d 42 1d 6b 52"
```
