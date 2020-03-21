---
title: 追加のクラス ライブラリと API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
ms.topic: conceptual
ms.openlocfilehash: abf7fd20988ebaaaf1a40ccc168c636fd0dacc1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155909"
---
# <a name="additional-class-libraries-and-apis"></a>追加のクラス ライブラリと API

.NET フレームワークは常に進化しています。 クロスプラットフォーム開発を改善し、新機能を早期に導入するために、新しい機能は帯域外にリリースされます (OOB). ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。  
  
さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。 たとえば、<xref:System.Text.CodePagesEncodingProvider>このクラスは、.NET Framework を使用して開発された UWP アプリでコード ページエンコーディングを使用できるようにします。 ここでは、これらのライブラリの一覧も示します。  
  
## <a name="oob-projects"></a>OOB プロジェクト
  
| Project | 説明 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。 |
| <xref:System.Net.Http.WinHttpHandler> | Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。 |
| <xref:System.Numerics> | SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。|
| <xref:System.Threading.Tasks.Dataflow> | TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、コンカレンシー対応アプリケーションの堅牢性を強化します。 |  

## <a name="platform-specific-libraries"></a>プラットフォーム固有のライブラリ
  
| Project | 説明 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | ユニバーサル<xref:System.Text.EncodingProvider>Windows プラットフォームを対象とするアプリでコード ページエンコーディングを使用できるようにクラスを拡張します。 |  
  
## <a name="private-apis"></a>プライベート API  

この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。  
  
* [アイテム プロパティ](microsoft.sqlserver.server.smiorderproperty.item.md)
* [メソッドの例外](system.exception.prepforremoting.md)
* [プロパティを定義します。](system.data.sqltypes.sqlchars.stream.md)
* [コンストラクター](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [プロパティを検索します。](system.data.sqltypes.sqlstreamchars.canseek.md)
* [プロパティ](system.data.sqltypes.sqlstreamchars.isnull.md)
* [プロパティの長さ](system.data.sqltypes.sqlstreamchars.length.md)
* [メソッドを閉じる](system.data.sqltypes.sqlstreamchars.close.md)
* [メソッドを破棄します。](system.data.sqltypes.sqlstreamchars.dispose.md)
* [メソッドをフラッシュします。](system.data.sqltypes.sqlstreamchars.flush.md)
* [メソッドを読み取る](system.data.sqltypes.sqlstreamchars.read.md)
* [メソッドを検索します。](system.data.sqltypes.sqlstreamchars.seek.md)
* [メソッドを設定します。](system.data.sqltypes.sqlstreamchars.setlength.md)
* [メソッドの書き込み](system.data.sqltypes.sqlstreamchars.write.md)
* [メソッドを取得します。](system.io.memorystream.internalgetoriginandlength.md)
* [接続クラス](connection.md)
* [フィールドを\_書き込む](m_writelist.md)
* [クラス](connectiongroup.md)
* [\_接続リスト フィールド](m_connectionlist.md)
* [接続プロパティ](system.net.connectstream.connection.md)
* [クラス](coreresponsedata.md)
* [\_応答ヘッダー フィールド](coreresponsedata_m_responseheaders.md)
* [\_ステータスコード フィールド](coreresponsedata_m_statuscode.md)
* [を指定します。\_自動リダイレクトフィールド](_autoredirects.md)
* [を指定します。\_コアレスポンスフィールド](httpwebrequest__coreresponse.md)
* [を指定します。\_応答フィールド](_httpresponse.md)
* [プロパティ](system.net.pooledstream.networkstream.md)
* [クラス](system.net.rtcstate.md)
* [\_接続グループリスト フィールド](m_connectiongrouplist.md)
* [サービスポイント\_テーブル フィールド](s_servicepointtable.md)
* [フィールドm_Worker](system.net.tlsstream.m_worker.md)
* [プロパティ](system.net.security.sslstate.sslprotocol.md)
* [メソッド](system.servicemodel.channels.message.bodytostring.md)
* [メソッドを使用します。](system.servicemodel.channels.message.writestartheaders.md)
* [\_フィールドをテストする](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [クラス.Windows.フォーム.デザイン.データメンバーフィールドエディタ](datamemberfieldeditor-class.md)
* [クラスをデザインします。](datamemberlisteditor-class.md)
* [メソッド](system.xml.xmlreader.createsqlreader.md)
* [Adodb。接続インターフェイス](adodb.connection.md)
* [Adodb。イベント理由列挙](adodb.eventreasonenum.md)
* [Adodb。イベントステータス列挙](adodb.eventstatusenum.md)
* [ストドール。ディスイスパムス構造](stdole.dispparams.md)
* [ストドール。エクスセプインフォ構造](stdole.excepinfo.md)
* [ストドール。IFont.Nameプロパティ](stdole.ifont.name.md)
* [ストドール。インターフェイス](stdole.ifontdisp.md)
* [ストドール。プロパティを処理します。](stdole.ipicture.handle.md)
* [ストドール。プロパティを処理します。](stdole.ipicturedisp.handle.md)
* [ストドール。Std フォント インターフェイス](stdole.stdfont.md)
* [ストドール。StdPicture インターフェイス](stdole.stdpicture.md)
  
## <a name="see-also"></a>関連項目

* [.NET Framework および OOB リリース](../get-started/the-net-framework-and-out-of-band-releases.md)
