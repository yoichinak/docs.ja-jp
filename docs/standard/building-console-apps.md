---
title: ".NET Framework におけるコンソール アプリケーションの構築"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4e0bc3f14a3d21776506f0a269a1a8c9f970cac0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="building-console-applications-in-the-net-framework"></a>.NET Framework におけるコンソール アプリケーションの構築
.NET Framework のアプリケーションは、<xref:System.Console?displayProperty=nameWithType> クラスを使用して、コンソールから文字を読み取り、コンソールに文字を書き込みます。 コンソールからのデータは標準入力ストリームから読み取られ、コンソールへのデータは標準出力ストリームに書き込まれ、コンソールへのエラー データは標準エラー出力ストリームに書き込まれます。 これらのストリームは、アプリケーションの起動時に自動的にコンソールに関連付けられ、それぞれ <xref:System.Console.In%2A> プロパティ、<xref:System.Console.Out%2A> プロパティ、および <xref:System.Console.Error%2A> プロパティとして示されます。  
  
 <xref:System.Console.In%2A?displayProperty=nameWithType> プロパティの値が <xref:System.IO.TextReader?displayProperty=nameWithType> オブジェクトであるのに対し、<xref:System.Console.Out%2A?displayProperty=nameWithType> および <xref:System.Console.Error%2A?displayProperty=nameWithType> プロパティの値は <xref:System.IO.TextWriter?displayProperty=nameWithType> オブジェクトです。 これらのプロパティを、コンソールを表さないストリームに関連付けることがができます。これにより、ストリームの出力先または入力元として異なる位置を指定できます。 たとえば、<xref:System.Console.Out%2A?displayProperty=nameWithType> プロパティを <xref:System.Console.SetOut%2A?displayProperty=nameWithType> メソッドで <xref:System.IO.FileStream?displayProperty=nameWithType> をカプセル化する <xref:System.IO.StreamWriter?displayProperty=nameWithType> に設定することにより、出力をファイルにリダイレクトできます。 <xref:System.Console.In%2A?displayProperty=nameWithType> プロパティと <xref:System.Console.Out%2A?displayProperty=nameWithType> プロパティとが同じストリームを参照する必要はありません。  
  
> [!NOTE]
>  コンソール アプリケーション (C#、Visual Basic、および C++ の例を含む) をビルドする方法の詳細については <xref:System.Console> クラスのドキュメントを参照してください。  
  
 Windows ベースのアプリケーションなどでコンソールが存在しない場合には、情報を書き込む先のコンソールがないため、標準出力ストリームに書き込まれた出力を参照できません。 アクセスできないコンソールに情報を書き込んでも、例外は発生しません。  
  
 Visual Studio を使用して開発した Windows ベースのアプリケーション内で読み取りおよび書き込み用のコンソールを有効にするには、プロジェクトの **[プロパティ]** ダイアログ ボックスを開き、**[アプリケーション]** タブをクリックして、**[アプリケーションの種類]** を **[コンソール アプリケーション]** に設定します。  
  
 コンソール アプリケーションには、既定で起動されるメッセージ ポンプがありません。 したがって、コンソールが Microsoft Win32 タイマーを呼び出すと、失敗する場合があります。  
  
 **System.Console** クラスには、コンソールから個々の文字または行全体を読み取ることができるメソッドがあります。 その他のメソッドは、まずデータと書式指定文字列を変換してから、書式設定された文字列をコンソールに書き込みます。 書式指定文字列の詳細については、「[Formatting Types](../../docs/standard/base-types/formatting-types.md)」(型の書式設定) を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Console?displayProperty=nameWithType>  
 [型の書式設定](../../docs/standard/base-types/formatting-types.md)
