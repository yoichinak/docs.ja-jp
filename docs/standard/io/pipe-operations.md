---
title: .NET のパイプ操作
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- pipes [.NET Framework]
- pipe operations [.NET Framework]
- interprocess communication [.NET Framework], pipes
- I/O [.NET Framework], pipes
ms.assetid: 7b964ebd-7a4f-4d28-8194-7841f9e4c702
ms.openlocfilehash: a634cb87a5f25b520e5fe6fd5b39eae861120a28
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278689"
---
# <a name="pipe-operations-in-net"></a>.NET のパイプ操作
パイプは、プロセス間通信の手段となります。 パイプには、2 種類あります。  
  
- 匿名パイプ。  
  
     匿名パイプは、ローカル コンピューターでのプロセス間通信を実現します。 匿名パイプは、名前付きパイプより必要なオーバーヘッドは少ないですが、提供するサービスは限られています。 匿名パイプは一方向であり、ネットワーク経由で使用することはできません。 これでは、1 つのサーバー インスタンスのみをサポートしています。 匿名パイプは、スレッド間、またはパイプ ハンドルを作成時に子プロセスに簡単に渡すことができる親と子のプロセス間の通信で便利です。  
  
     .NET では、<xref:System.IO.Pipes.AnonymousPipeServerStream> クラスと <xref:System.IO.Pipes.AnonymousPipeClientStream> クラスを使用して匿名パイプを実装します。  
  
     「[方法: ローカルのプロセス間通信で匿名パイプを使用する](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)」を参照してください。  
  
- 名前付きパイプ。  
  
     名前付きパイプは、パイプ サーバーと 1 つ以上のパイプ クライアントとの間でのプロセス間通信を提供します。 名前付きパイプは、一方向であることも、双方向であることも可能です。 これでは、メッセージ ベースの通信がサポートされ、同じパイプ名を使用して複数のクライアントが同時にサーバー プロセスに接続することができます。 名前付きパイプでは、プロセスを接続してリモート サーバーで独自のアクセス許可を使用する、偽装もサポートしています。  
  
     .NET では、<xref:System.IO.Pipes.NamedPipeServerStream> クラスと <xref:System.IO.Pipes.NamedPipeClientStream> クラスを使用して名前付きパイプを実装します。  
  
     「[方法: ネットワークのプロセス間通信で名前付きパイプを使用する](how-to-use-named-pipes-for-network-interprocess-communication.md)」を参照してください。  
  
## <a name="see-also"></a>参照

- [ファイルおよびストリーム入出力](index.md)
- [方法: ローカルのプロセス間通信で匿名パイプを使用する](how-to-use-anonymous-pipes-for-local-interprocess-communication.md)
- [方法: ネットワークのプロセス間通信で名前付きパイプを使用する](how-to-use-named-pipes-for-network-interprocess-communication.md)
