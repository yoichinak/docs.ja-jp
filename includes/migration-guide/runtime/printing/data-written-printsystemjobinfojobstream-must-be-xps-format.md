---
ms.openlocfilehash: 74f00821f2304664729faa8de2f0163c6611f513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "66379582"
---
### <a name="data-written-to-printsystemjobinfojobstream-must-be-in-xps-format"></a>PrintSystemJobInfo.JobStream に書き込まれるデータは XPS 形式とする必要があります

|   |   |
|---|---|
|説明|<xref:System.Printing.PrintSystemJobInfo.JobStream> プロパティにより印刷ジョブのストリームが公開されます。 ユーザーが基になるオペレーティング システム印刷コンポーネントに生のデータを送信するには、このストリームにデータを書き込みを行います。 .NET Framework 4.5 以降、Windows 8 より後のバージョンの Windows オペレーティング システムでは、このストリームに書き込むデータは XPS 形式のパッケージ ストリームにする必要があります。|
|提案される解決策|印刷内容を出力するには、次のいずれかの操作を行います。<ul><li><xref:System.Windows.Xps.XpsDocumentWriter> クラスを使用して印刷内容を出力します。 これが、推奨される方法です。</li><li><xref:System.Printing.PrintSystemJobInfo.JobStream> プロパティによって返されるストリームに送信されるデータを、XPS 形式のパッケージ ストリームにします。</li></ul>|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Printing.PrintSystemJobInfo.JobStream?displayProperty=nameWithType></li></ul>|
