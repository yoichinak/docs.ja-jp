---
title: Windows Communication Foundation の採用
ms.date: 03/30/2017
ms.assetid: 49ba71e2-9468-4082-84c5-cf8daf95e34a
ms.openlocfilehash: 58a51f7ea0db2297c7151a752de3f54307e0c5fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857715"
---
# <a name="adopting-windows-communication-foundation"></a>Windows Communication Foundation の採用

ASP.NET を使用して開発された既存のアプリケーションのメンテナンスを続行中に、新たに開発、Windows Communication Foundation (WCF) を使用することができます。 WCF はどのようなシナリオでの .NET Framework でビルドされたアプリケーションとの通信を促進するため、最適な選択をするとしているため、として使用できるさまざまな方法でソフトウェア通信の問題を解決するための標準的なツールを ASP.NETできません。

新しい WCF アプリケーションは、既存の ASP.NET Web サービスと同じマシンにデプロイできます。 既存の ASP.NET Web サービス、.NET Framework バージョン 2.0 より前のバージョンを使う場合は、選択的に新しい WCF アプリケーションがホストする IIS アプリケーションを .NET Framework 2.0 を展開する、ASP.NET IIS 登録ツールを使用できます。 そのツールについては、 [ASP.NET IIS 登録ツール (Aspnet_regiis.exe)](https://go.microsoft.com/fwlink/?LinkId=94687)、ユーザー インターフェイスは、IIS 6.0 管理コンソールに組み込まれているとします。

WCF サービスが IIS での既存の ASP.NET Web サービス アプリケーションを ASP.NET 互換モードで実行するように構成を追加することで、既存の ASP.NET Web サービスに新機能を追加する、WCF を使用できます。 新しい WCF サービスのコードにアクセスしを使用して既存の ASP.NET コードと同じアプリケーションの状態情報を更新する ASP.NET の互換モードにより、<xref:System.Web.HttpContext>クラス。 また、アプリケーションは同じクラス ライブラリを共有することもできます。

WCF クライアントは、ASP.NET Web サービスを使用できます。 WCF サービスで構成されている、 <xref:System.ServiceModel.BasicHttpBinding> ASP.NET Web サービス クライアントで使用されることができます。 ASP.NET Web サービスは、WCF アプリケーションと共存させることができ、WCF は、既存の ASP.NET Web サービスに機能を追加も使用できます。 これで WCF と ASP.NET Web サービスを組み合わせて使用する次の方法を考えると、WCF としない ASP.NET Web サービスによって提供される機能を必要とする場合にのみ、ASP.NET Web サービスを WCF に移行することがあります。

必要があるいくつかの場合でも別に 1 つのテクノロジからコードの移行は、適切なアプローチではめったにありません。 以前のテクノロジでは満たされない新しい要件を満たすために新しいテクノロジを採用する場合、新たに拡張された要件を満たす新しいソリューションを設計することが正しい方法です。 新しい設計では、既存のシステムでの経験とそのシステムを設計して以来、獲得した知識を活用できます。 また、新しい設計は、新しいプラットフォーム上で古い設計を再制作するのではなく、新しいテクノロジの機能を十分に活用することができます。 新しい設計の主要な要素のプロトタイプが完成すると、既存のシステムのコードを新しいシステム内で再使用することが容易になります。

## <a name="see-also"></a>関連項目

- [方法: メタデータの取得および準拠サービスの実装](../../../../docs/framework/wcf/feature-details/how-to-retrieve-metadata-and-implement-a-compliant-service.md)
