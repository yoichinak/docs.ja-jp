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
ms.openlocfilehash: 0aed6f32bbd3ffdc9446e9d17be2d90c62444ee1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053242"
---
# <a name="additional-class-libraries-and-apis"></a>追加のクラス ライブラリと API

.NET Framework は絶えず進化しています。 クロスプラットフォームの開発を改善し、新しい機能を早期に導入するために、新機能がアウトオブバンド (OOB) でリリースされます。 ここでは、ドキュメントが用意されている OOB プロジェクトの一覧を示します。  
  
さらに、いくつかのライブラリは、特定のプラットフォームまたは .NET Framework の実装を対象にしています。 たとえば<xref:System.Text.CodePagesEncodingProvider> 、クラスを使用すると、.NET Framework を使用して開発された UWP アプリでコードページエンコーディングを使用できるようになります。 ここでは、これらのライブラリの一覧も示します。  
  
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
| <xref:System.Text.CodePagesEncodingProvider> | <xref:System.Text.EncodingProvider>クラスを拡張して、ユニバーサル Windows プラットフォームを対象とするアプリでコードページエンコーディングを使用できるようにします。 |  
  
## <a name="private-apis"></a>プライベート API  

この API は製品インフラストラクチャをサポートします。コードから直接使用することはできません。  
  
| API 名 |
| -------- |
| [System .Net. Connection クラス](connection.md) |
| [System .net. 接続. m\_writelist フィールド](m_writelist.md) |
| [システム .Net. ConnectionGroup クラス](connectiongroup.md) |
| [System .net. connectiongroup. m\_connectiongroup フィールド](m_connectionlist.md) |
| [CoreResponseData クラス](coreresponsedata.md) |
| [System.Net.CoreResponseData.m\_ResponseHeaders Field](coreresponsedata_m_responseheaders.md) |
| [CoreResponseData の\_StatusCode フィールド](coreresponsedata_m_statuscode.md) |
| [HttpWebRequest。\_Autoredirects フィールド](_autoredirects.md) |
| [HttpWebRequest。\_CoreResponse フィールド](httpwebrequest__coreresponse.md) |
| [HttpWebRequest。\_Httpresponse.cache フィールド](_httpresponse.md) |
| [System.Net.ServicePoint.m\_ConnectionGroupList Field](m_connectiongrouplist.md) |
| [System.Net.ServicePointManager.s\_ServicePointTable Field](s_servicepointtable.md) |
| [System.Windows.Diagnostics.VisualDiagnostics.s\_isDebuggerCheckDisabledForTestPurposes Field](s-isdebuggercheckdisabledfortestpurposes-field.md) |
| [System.Windows.Forms.Design.DataMemberFieldEditor Class](datamemberfieldeditor-class.md) |
| [System.Windows.Forms.Design.DataMemberListEditor Class](datamemberlisteditor-class.md) |
  
## <a name="see-also"></a>関連項目

- [NET Framework および特別なリリース](../get-started/the-net-framework-and-out-of-band-releases.md)
