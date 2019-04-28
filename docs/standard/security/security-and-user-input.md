---
title: セキュリティとユーザー入力
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- security [.NET Framework], user input
- user input, security
- secure coding, user input
- code security, user input
ms.assetid: 9141076a-96c9-4b01-93de-366bb1d858bc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 27818d5e1779cd6e10e11830f91a20a3e638639a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933784"
---
# <a name="security-and-user-input"></a>セキュリティとユーザー入力
ユーザー データにはあらゆる種類の入力 (Web 要求または URL からのデータや、Microsoft Windows Forms アプリケーションのコントロールへの入力など) がありますが、これはコードに悪影響を及ぼすことがあります。このようなデータはパラメーターとして直接使用され、他のコードを呼び出す場合が多いためです。 この状況は、悪意のあるコードが不明なパラメーターを使用してコードを呼び出すことと似ており、同じ予防策をとる必要があります。 実際には、ユーザー入力の安全性を保つ方が困難です。潜在的に信頼されていないデータの存在をトレースするスタック フレームがないためです。  
  
 これらは最も微小で見つけにくいセキュリティ バグです。セキュリティとは無関係に見えるコードに存在すことができ、他のコードに悪いデータを送り出すゲートウェイだからです。 このようなバグを探し出すには、あらゆる種類の入力データを追跡し、可能性のある値の範囲を想像し、そのデータを扱うコードがすべてのケースを処理できるかどうかを検討します。 これらのバグは、範囲チェックを使用して、コードで処理できない入力を拒否することで修正できます。  
  
 ユーザー データに関連する重要な注意事項を次に示します。  
  
- サーバー応答内のすべてのユーザー データは、クライアント上でサーバーのサイトのコンテキストで実行されます。 ご使用の Web サーバーがユーザー データを受け取り、返す Web ページにそのデータを挿入する場合、たとえば、そのデータが **\<script>** タグを組み込んで、サーバーからのように実行する可能性があります。  
  
- クライアントはすべての URL を要求できることに注意してください。  
  
- 巧妙なパスまたは無効なパスに注意してください。  
  
    - ..\、極端に長いパス。  
  
    - ワイルドカード文字 (*) の使用。  
  
    - トークンの展開 (%token%)。  
  
    - 特別な意味を持つ変わった形式のパス。  
  
    - 代替ファイル システム ストリーム名、`filename::$DATA` など。  
  
    - ファイル名の短縮バージョン、`longfilename`に対して `longfi~1` など。  
  
- Eval(userdata) は何でも実行できることに注意してください。  
  
- ユーザー データを含む名前の遅延バインディングを警戒してください。  
  
- Web データを扱う場合は、許容されるさまざまな形式のエスケープを検討してください。  
  
    - 16 進数エスケープ (%nn)。  
  
    - Unicode エスケープ (%nnn)。  
  
    - オーバーロング UTF-8 エスケープ (%nn%nn)。  
  
    - ダブル エスケープ (%nn が %mmnn になります。%mm は '%' のエスケープです)。  
  
- 標準形式が複数あるユーザー名に注意してください。 たとえば、よく使用するのは MYDOMAIN\\*username* 形式または *username*@mydomain.example.com 形式です。  
  
## <a name="see-also"></a>関連項目

- [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
