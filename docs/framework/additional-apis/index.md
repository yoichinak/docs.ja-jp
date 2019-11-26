---
title: 追加のクラス ライブラリと API
ms.date: 11/19/2019
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: e1e2af584c73b1c0b2548cdd3fcbd8517dfa330d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429345"
---
# <a name="additional-class-libraries-and-apis"></a>追加のクラス ライブラリと API

The .NET Framework is constantly evolving. To improve cross-platform development and introduce new functionality early, new features are released out of band (OOB). ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。  
  
さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。 For example, the <xref:System.Text.CodePagesEncodingProvider> class makes code page encodings available to UWP apps developed using the .NET Framework. ここでは、これらのライブラリの一覧も示します。  
  
## <a name="oob-projects"></a>OOB プロジェクト
  
| [プロジェクト] | 説明 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。 |
| <xref:System.Net.Http.WinHttpHandler> | Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。 |
| <xref:System.Numerics> | SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。| 
| <xref:System.Threading.Tasks.Dataflow> | TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、コンカレンシー対応アプリケーションの堅牢性を強化します。 |  

## <a name="platform-specific-libraries"></a>プラットフォーム固有のライブラリ
  
| [プロジェクト] | 説明 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | Extends the <xref:System.Text.EncodingProvider> class to make code page encodings available to apps that target the Universal Windows Platform. |  
  
## <a name="private-apis"></a>プライベート API  

この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。  
  
* [Microsoft.SqlServer.Server.SmiOrderProperty.Item Property](microsoft.sqlserver.server.smiorderproperty.item.md)
* [System.Exception.PrepForRemoting Method](system.exception.prepforremoting.md)
* [System.Data.SqlTypes.SqlChars.Stream Property](system.data.sqltypes.sqlchars.stream.md)
* [System.Data.SqlTypes.SqlStreamChars Constructor](system.data.sqltypes.sqlstreamchars.-ctor.md)
* [System.Data.SqlTypes.SqlStreamChars.CanSeek Property](system.data.sqltypes.sqlstreamchars.canseek.md)
* [System.Data.SqlTypes.SqlStreamChars.IsNull Property](system.data.sqltypes.sqlstreamchars.isnull.md)
* [System.Data.SqlTypes.SqlStreamChars.Length Property](system.data.sqltypes.sqlstreamchars.length.md)
* [System.Data.SqlTypes.SqlStreamChars.Close Method](system.data.sqltypes.sqlstreamchars.close.md)
* [System.Data.SqlTypes.SqlStreamChars.Dispose Method](system.data.sqltypes.sqlstreamchars.dispose.md)
* [System.Data.SqlTypes.SqlStreamChars.Flush Method](system.data.sqltypes.sqlstreamchars.flush.md)
* [System.Data.SqlTypes.SqlStreamChars.Read Method](system.data.sqltypes.sqlstreamchars.read.md)
* [System.Data.SqlTypes.SqlStreamChars.Seek Method](system.data.sqltypes.sqlstreamchars.seek.md)
* [System.Data.SqlTypes.SqlStreamChars.SetLength Method](system.data.sqltypes.sqlstreamchars.setlength.md)
* [System.Data.SqlTypes.SqlStreamChars.Write Method](system.data.sqltypes.sqlstreamchars.write.md)
* [System.IO.MemoryStream.InternalGetOriginAndLength Method](system.io.memorystream.internalgetoriginandlength.md)
* [System.Net.Connection Class](connection.md)
* [System.Net.Connection.m\_WriteList Field](m_writelist.md)
* [System.Net.ConnectionGroup Class](connectiongroup.md)
* [System.Net.ConnectionGroup.m\_ConnectionList Field](m_connectionlist.md)
* [System.Net.ConnectStream.Connection Property](system.net.connectstream.connection.md)
* [System.Net.CoreResponseData Class](coreresponsedata.md)
* [System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md)
* [System.Net.CoreResponseData.m\_StatusCode Field](coreresponsedata_m_statuscode.md)
* [System.Net.HttpWebRequest.\_AutoRedirects Field](_autoredirects.md)
* [System.Net.HttpWebRequest.\_CoreResponse Field](httpwebrequest__coreresponse.md)
* [System.Net.HttpWebRequest.\_HttpResponse Field](_httpresponse.md)
* [System.Net.PooledStream.NetworkStream Property](system.net.pooledstream.networkstream.md)
* [System.Net.RtcState class](system.net.rtcstate.md)
* [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md)
* [System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md)
* [System.Net.TlsStream.m_Worker Field](system.net.tlsstream.m_worker.md)
* [System.Net.Security.SslState.SslProtocol Property](system.net.security.sslstate.sslprotocol.md)
* [System.ServiceModel.Channels.Message.BodyToString Method](system.servicemodel.channels.message.bodytostring.md)
* [System.ServiceModel.Channels.Message.WriteStartHeaders Method](system.servicemodel.channels.message.writestartheaders.md)
* [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md)
* [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md)
* [System.Windows.Forms.Design.DataMemberListEditor Class](datamemberlisteditor-class.md)
* [System.Xml.XmlReader.CreateSqlReader Method](system.xml.xmlreader.createsqlreader.md)
* [adodb.Connection Interface](adodb.connection.md)
* [adodb.EventReason Enum](adodb.eventreasonenum.md)
* [adodb.EventStatus Enum](adodb.eventstatusenum.md)
* [stdole.DISPPARAMS Structure](stdole.dispparams.md)
* [stdole.EXCEPINFO Structure](stdole.excepinfo.md)
* [stdole.IFont.Name Property](stdole.ifont.name.md)
* [stdole.IFontDisp Interface](stdole.ifontdisp.md)
* [stdole.IPicture.Handle Property](stdole.ipicture.handle.md)
* [stdole.IPictureDisp.Handle Property](stdole.ipicturedisp.handle.md)
* [stdole.StdFont Interface](stdole.stdfont.md)
* [stdole.StdPicture Interface](stdole.stdpicture.md)
  
## <a name="see-also"></a>関連項目

* [NET Framework および特別なリリース](../get-started/the-net-framework-and-out-of-band-releases.md)
