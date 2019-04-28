---
title: 追加のクラス ライブラリと API
ms.date: 01/29/2018
helpviewer_keywords:
- Additional class libraries
- Additional managed libraries
- .NET Framework out-of-band releases
- out-of-band releases
ms.assetid: cf2d9006-b631-4e5d-81cd-20aab78c60f1
author: mairaw
ms.author: mairaw
ms.topic: conceptual
ms.openlocfilehash: a48a145cd337a18c4ce63b281e1c82032d0532e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675365"
---
# <a name="additional-class-libraries-and-apis"></a>追加のクラス ライブラリと API

.NET Framework は絶えず進化しています。 クロス プラットフォーム開発を向上させ、新しい機能を早期導入、新機能はアウトオブ バンド (OOB) リリースします。 ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。  
  
さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。 たとえば、<xref:System.Text.CodePagesEncodingProvider>クラスが .NET Framework を使用して開発された UWP アプリで使用できるコード ページ エンコーディングを使用します。 ここでは、これらのライブラリの一覧も示します。  
  
## <a name="oob-projects"></a>OOB プロジェクト
  
| プロジェクト | 説明 |  
| ------- | ----------- |  
| <xref:System.Collections.Immutable> | スレッド セーフであり、内容が変更されないことが保証されているコレクションを提供します。 |
| <xref:System.Net.Http.WinHttpHandler> | Windows の WinHTTP インターフェイスに基づいた <xref:System.Net.Http.HttpClient> のメッセージ ハンドラーを提供します。 |
| <xref:System.Numerics> | SIMD ハードウェア ベースのアクセラレータを利用できるベクター型のライブラリを提供します。| 
| <xref:System.Threading.Tasks.Dataflow> | TPL データフロー ライブラリはデータ フロー コンポーネントを提供し、コンカレンシー対応アプリケーションの堅牢性を強化します。 |  

## <a name="platform-specific-libraries"></a>プラットフォーム固有のライブラリ
  
| プロジェクト | 説明 |  
| ------- | ----------- |  
| <xref:System.Text.CodePagesEncodingProvider> | 拡張、<xref:System.Text.EncodingProvider>クラスのコード ページ エンコーディングをユニバーサル Windows プラットフォームを対象とするアプリを使用できるようにします。 |  
  
## <a name="private-apis"></a>プライベート API  

この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。  
  
| API 名 |
| -------- |
| [System.Net.Connection クラス](../../../docs/framework/additional-apis/connection.md) |
| [System.Net.Connection.m\_WriteList フィールド](../../../docs/framework/additional-apis/m_writelist.md) |
| [System.Net.ConnectionGroup クラス](../../../docs/framework/additional-apis/connectiongroup.md) |
| [System.Net.ConnectionGroup.m\_ConnectionList フィールド](../../../docs/framework/additional-apis/m_connectionlist.md) |
| [System.Net.CoreResponseData クラス](../../../docs/framework/additional-apis/coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](../../../docs/framework/additional-apis/coreresponsedata_m_responseheaders.md) |
| [System.Net.CoreResponseData.m\_StatusCode フィールド](../../../docs/framework/additional-apis/coreresponsedata_m_statuscode.md) |
| [System.Net.HttpWebRequest します。\_AutoRedirects フィールド](../../../docs/framework/additional-apis/_autoredirects.md) |
| [System.Net.HttpWebRequest します。\_CoreResponse フィールド](../../../docs/framework/additional-apis/httpwebrequest__coreresponse.md) |
| [System.Net.HttpWebRequest します。\_HttpResponse フィールド](../../../docs/framework/additional-apis/_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](../../../docs/framework/additional-apis/m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](../../../docs/framework/additional-apis/s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](../../../docs/framework/additional-apis/s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](../../../docs/framework/additional-apis/datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](../../../docs/framework/additional-apis/datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>関連項目

- [NET Framework および特別なリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)
