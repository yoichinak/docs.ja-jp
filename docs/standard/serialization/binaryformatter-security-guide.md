---
title: BinaryFormatter セキュリティ ガイド
description: この記事では、BinaryFormatter 型に固有のセキュリティ上のリスクと、さまざまなシリアライザーで使用すべき推奨事項について説明します。
ms.date: 07/11/2020
ms.author: levib
author: GrabYourPitchforks
ms.openlocfilehash: f6a54b34bbf1e19212fe37aadb448a1722fe9ff0
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/17/2020
ms.locfileid: "86444750"
---
# <a name="binaryformatter-security-guide"></a>BinaryFormatter セキュリティ ガイド

この記事は、次の .NET 実装に適用されます。

* .NET Framework (すべてのバージョン)
* .NET Core 2.1 - 3.1
* .NET 5.0 以降

## <a name="background"></a>背景

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 型は危険であり、データ処理用としては "***推奨されません***"。 アプリケーションでは、処理するデータが信頼できると思われる場合でも、できるだけ早く `BinaryFormatter` の使用をやめる必要があります。 `BinaryFormatter` は安全ではなく、安全にすることはできません。

この記事は、次の型に適用されます。

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Web.UI.ObjectStateFormatter>

逆シリアル化の脆弱性は、要求ペイロードが安全でない方法で処理される脅威のカテゴリです。 攻撃者がこのような脆弱性をアプリに対して利用することに成功すると、サービス拒否 (DoS)、情報漏えい、またはターゲット アプリ内でのリモート コード実行が発生する可能性があります。 このリスク カテゴリは、常に [OWASP Top 10](https://owasp.org/www-project-top-ten/) に入っています。 ターゲットには、C/C++、Java、C# などの[さまざまな言語](https://owasp.org/www-community/vulnerabilities/Deserialization_of_untrusted_data)で記述されたアプリが含まれます。

.NET では、最大のリスクのターゲットは、<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> 型を使用してデータを逆シリアル化するアプリです。 `BinaryFormatter` は、強力で使いやすいため、.NET エコシステム全体で幅広く使用されています。 ただし、この同じ機能を使用して、攻撃者はターゲット アプリ内の制御フローに影響を与えることができます。 攻撃が成功すると、攻撃者はターゲット プロセスのコンテキスト内でコードを実行できるようになります。

単純な例えとして、ペイロードに対して `BinaryFormatter.Deserialize` を呼び出すことは、そのペイロードをスタンドアロンの実行可能ファイルとして解釈して起動することと同じです。

## <a name="binaryformatter-security-vulnerabilities"></a>BinaryFormatter のセキュリティの脆弱性

> [!WARNING]
> `BinaryFormatter.Deserialize` メソッドは、信頼されていない入力で使用するときは__決して__安全ではありません。 代わりにこの記事で後述する代替手段のいずれかの使用を検討することを強くお勧めします。

`BinaryFormatter` が実装されたのは、逆シリアル化の脆弱性が脅威カテゴリとしてよく理解される前でした。 このため、そのコードは最新のベスト プラクティスに従っていません。 `Deserialize` メソッドは、利用側アプリに対して攻撃者が DoS 攻撃を実行するためのベクトルとして使用できます。 これらの攻撃によって、アプリが応答しなくなったり、予期しないプロセスの終了が発生したりする可能性があります。 このカテゴリの攻撃は、`SerializationBinder` またはその他の `BinaryFormatter` 構成スイッチを使用して軽減することはできません。 .NET では、この動作を "***仕様***" と見なし、動作を変更するためのコード更新は発行されません。

`BinaryFormatter.Deserialize` は、情報の漏えいやリモート コード実行など、他の攻撃カテゴリに対して脆弱な場合があります。 カスタムの <xref:System.Runtime.Serialization.SerializationBinder> などの機能を使用しても、これらのリスクを適切に軽減するには不十分な可能性があります。 .NET でセキュリティ更新プログラムを実質的に公開できない新しい脆弱性が検出される可能性があります。 コンシューマーは、個々のシナリオを評価し、これらのリスクに対する潜在的な危険を検討する必要があります。

`BinaryFormatter` を利用している場合は、アプリで個々のリスク評価を実行することをお勧めします。 `BinaryFormatter` を利用するかどうかの判断に関する責任は、すべてコンシューマーにあります。 コンシューマーは、`BinaryFormatter` の使用に関するセキュリティ、技術、評判、法律、規制の要件を評価する必要があります。

## <a name="preferred-alternatives"></a>推奨される代替手段

.NET には、信頼されていないデータを安全に処理できるいくつかの付属シリアライザーが用意されています。

* <xref:System.Xml.Serialization.XmlSerializer> と <xref:System.Runtime.Serialization.DataContractSerializer> (オブジェクト グラフを XML との間でシリアル化するためのもの)。 `DataContractSerializer` と <xref:System.Runtime.Serialization.NetDataContractSerializer> を混同しないようにしてください。
* <xref:System.IO.BinaryReader> と <xref:System.IO.BinaryWriter> (XML および JSON 向け)。
* <xref:System.Text.Json> API (オブジェクト グラフを JSON にシリアル化するためのもの)。

## <a name="dangerous-alternatives"></a>危険な代替手段

次のシリアライザーは避けてください。

* <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
* <xref:System.Web.UI.LosFormatter>
* <xref:System.Runtime.Serialization.NetDataContractSerializer>
* <xref:System.Web.UI.ObjectStateFormatter>

上記のシリアライザーはすべて、無制限のポリモーフィックな逆シリアル化を実行し、`BinaryFormatter` と同様に危険です。

## <a name="the-risks-of-assuming-data-to-be-trustworthy"></a>データを信頼できるものと想定するリスク

しばしばアプリ開発者は、信頼された入力のみを処理していると考えることがあります。 安全な入力という条件は、一部のまれな状況では真です。 しかし、開発者が気付かないうちにペイロードが信頼の境界を越えることの方が、より一般的です。

従業員がワークステーションからデスクトップ クライアントを使用してサービスを操作する__オンプレミス サーバーについて考えてみます__。 このシナリオは、`BinaryFormatter` の使用が許容される "安全な" 環境として単純に見られる場合があります。 ただし、このシナリオは、1 人の従業員のコンピューターにアクセスできれば企業全体への拡散が可能になるマルウェアのベクトルを示しています。 そのマルウェアは、企業で `BinaryFormatter` が使用されていることを利用して、従業員のワークステーションからバックエンド サーバーに横方向に移動できます。 その後、会社の機密データを抜き取ることができます。 このようなデータには、取引先の機密情報や顧客データが含まれます。

__保存状態を保持するために `BinaryFormatter` を使用するアプリについても検討してみます。__ これは、自前のハード ドライブ上のデータを読み書きすることは軽微な脅威を表すため、最初は安全なシナリオであるように思えます。 ただし、電子メールまたはインターネットでドキュメントを共有することは一般的です。ほとんどのエンド ユーザーは、これらのダウンロードしたファイルを開くことを危険な動作として認識していません。

このシナリオは、不正な効果を得るために利用できます。 アプリがゲームである場合、保存ファイルを共有しているユーザーは、知らずに危険にさらされます。 開発者自身もターゲットになり得ます。 攻撃者は、悪意のあるデータ ファイルを添付した電子メールを開発者のテクニカル サポートに送信し、サポート スタッフにそのファイルを開くように依頼するかもしれません。 この種の攻撃によって、攻撃者が企業に足掛かりを得る可能性があります。

もう 1 つのシナリオは、データ ファイルがクラウド ストレージに格納され、ユーザーのコンピューター間で自動的に同期される場合です。 クラウド ストレージ アカウントにアクセスできた攻撃者によって、データ ファイルが汚染される可能性があります。 このデータ ファイルは、ユーザーのコンピューターに自動的に同期されます。 次回ユーザーがデータ ファイルを開いたときに、攻撃者のペイロードが実行されます。 そのため、攻撃者はクラウド ストレージ アカウントの侵害を利用して、完全なコード実行アクセス許可を得ることができます。

__デスクトップ インストール モデルからクラウド ファースト モデルに移行するアプリを考えてみましょう。__ このシナリオには、デスクトップ アプリやリッチ クライアント モデルから Web ベースのモデルに移行するアプリが含まれます。 デスクトップ アプリ用に描かれた脅威モデルは、必ずしもクラウドベースのサービスに適用されるとは限りません。 デスクトップ アプリの脅威モデルでは、特定の脅威を "クライアントが自分自身を攻撃することは関心の対象ではない" として無視することがあります。 しかし、リモート ユーザー (クライアント) がクラウド サービス自体を攻撃していると見なされる場合、同じ脅威が関心の対象となる可能性があります。

> [!NOTE]
> 一般的に、シリアル化の目的は、オブジェクトをアプリの内外に送信することです。 脅威のモデル化の演習では、ほとんどの場合、この種類のデータ転送を信頼境界越えとしてマークします。

## <a name="further-resources"></a>他のリソース

* `BinaryFormatter` を利用しているアプリがどのように敵対者の攻撃を受けているかを調査するには、[YSoSerial.Net](https://github.com/pwntester/ysoserial.net) を参照してください。
* 脅威をモデル化するアプリとサービスに関する情報については、[脅威のモデル化](/securityengineering/sdl/threatmodeling)に関するページを参照してください。
* 逆シリアル化の脆弱性に関する一般的な背景情報:
  * [OWASP Top 10 - A8:2017-安全でない逆シリアル化](https://owasp.org/www-project-top-ten/OWASP_Top_Ten_2017/Top_10-2017_A8-Insecure_Deserialization)
  * [CWE-502: 信頼されていないデータの逆シリアル化](https://cwe.mitre.org/data/definitions/502.html)
