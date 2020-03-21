---
title: .NET Framework Data Provider for Oracle のシステム要件
ms.date: 03/30/2017
ms.assetid: 054f76b9-1737-43f0-8160-84a00a387217
ms.openlocfilehash: dab3378d3022c01c674640201a67f3bdbb4f571f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174252"
---
# <a name="system-requirements-for-the-net-framework-data-provider-for-oracle"></a>.NET Framework Data Provider for Oracle のシステム要件

.NET Framework Data Provider for Oracle を使用するには、MDAC (Microsoft Data Access Components) のバージョン 2.6 以降が必要です。 MDAC 2.8 SP1 をインストールすることをお勧めします。  
  
 Oracle 8i Release 3 (8.1.7) Client 以降もインストールする必要があります。  
  
 UTF16 は Oracle 9i の新機能なので、Oracle 9i 以前のバージョンの Oracle Client ソフトウェアでは UTF16 データベースにアクセスできません。 この機能を使用するには、お使いのクライアント ソフトウェアを Oracle 9i 以降にアップグレードする必要があります。  
  
## <a name="working-with-the-data-provider-for-oracle-and-unicode-data"></a>Data Provider for Oracle と Unicode データの使用  

以下は、Oracle および Oracle クライアント ライブラリの .NET Framework データ プロバイダーを使用する際に考慮する必要がある、Unicode 関連の問題の一覧です。 詳細については、Oracle のドキュメントを参照してください。  
  
### <a name="setting-the-unicode-value-in-a-connection-string-attribute"></a>接続文字列の属性に Unicode 値を設定する  

Oracle を操作する場合、接続文字列の属性を使用し、  
  
`Unicode=True`
  
UTF-16 モードで Oracle クライアント ライブラリを初期化することができます。 これにより、Oracle クライアント ライブラリで、マルチバイト文字列の代わりに UTF-16 (UCS-2 とよく似ています) が使用できるようになります。 新たに変換作業を行わなくても、Data Provider for Oracle で Oracle のコード ページを常に使用できます。 この構成は、Oracle 9i クライアントを使用して、AL16UTF16 の代替文字セットを持つ Oracle 9i データベースと通信する場合に動作します。 Oracle 9i クライアントが Oracle 9i サーバーと通信する場合、Unicode **CommandText**値を Oracle9i サーバーが使用する適切なマルチバイト文字セットに変換するために追加のリソースが必要です。 安全な構成が確保されていることがわかっている場合は、`Unicode=True` を接続文字列に追加することにより回避することができます。  
  
### <a name="mixing-versions-of-oracle-client-and-oracle-server"></a>Oracle クライアントと Oracle サーバーのバージョンの混在  

Oracle 8i クライアントは、サーバーの国別文字セットが AL16UTF16 (Oracle 9i のデフォルト設定) として指定されている場合、Oracle 9i データベースの NCHAR、NVARCHAR2、**または NCLOB**データにアクセスできません。 **NCHAR** **NVARCHAR2** UTF-16 文字セットのサポートは Oracle 9i まで導入されなかったため、Oracle 8i クライアントでは読み取れません。  
  
### <a name="working-with-utf-8-data"></a>UTF-8 データの使用  

代替文字セットを設定するには、レジストリ キー HKEY_LOCAL_MACHINE\SOFTWARE\ORACLE\HOMEID\NLS_LANG を UTF8 に設定します。 詳細については、ご使用のプラットフォームに関する Oracle のインストール ノートを参照してください。 既定の設定は、Oracle Client ソフトウェアのインストールに使用する言語の基本文字セットになっています。 接続するデータベースの各国語文字セットと言語が一致するように設定されていないと、パラメーターと列の組み合わせは、各国語文字セットではなくプライマリ データベースの文字セットでデータを送受信します。  
  
### <a name="oraclelob-can-only-update-full-characters"></a>OracleLob で更新できるのは Full 文字列のみです。  

使いやすさの理由から<xref:System.Data.OracleClient.OracleLob>、オブジェクトは .NET Framework ストリーム クラスから継承し **、ReadByte**メソッドと**WriteByte**メソッドを提供します。 また、Oracle **LOB**オブジェクトのセクションで動作する**CopyTo**や**Erase**などのメソッドも実装しています。 これに対し、Oracle クライアント ソフトウェアは、文字**LOB**(**CLOB**および**NCLOB**) を操作するための多くの API を提供します。 ただし、これらの API は full 文字列でのみ動作します。 この違いにより、Oracle 用データ プロバイダは、バイト単位で UTF-16 データを処理するための**読み取り**および**ReadByte**のサポートを実装します。 ただし **、OracleLob**オブジェクトの他のメソッドでは、フル文字操作のみが許可されます。  
  
## <a name="see-also"></a>関連項目

- [Oracle および ADO.NET](oracle-and-adonet.md)
- [ADO.NET の概要](ado-net-overview.md)
