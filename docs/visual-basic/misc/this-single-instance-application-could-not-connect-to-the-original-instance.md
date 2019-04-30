---
title: この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした
ms.date: 07/20/2015
f1_keywords:
- vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
ms.openlocfilehash: 7ffa9b185e16cfdf8223ce84e77d1a0e1fa67f65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942612"
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした
この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした。 この問題の考えられる原因の一部は次のとおりです。  
  
- 元のインスタンスが応答を停止した。  
  
- カーネル オブジェクトを作成するためのアクセス許可がアプリケーションにない。 カーネル オブジェクトの詳細については、次を参照してください。[ミュー テックス](../../standard/threading/mutexes.md)します。  
  
     カーネル オブジェクトの基本名は、アセンブリの GUID、メジャー バージョン番号、およびマイナー バージョン番号を連結したものです。 たとえば、基本名が `3639f15d-9547-43da-8145-60da347829915.1`になる可能性があります。  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>アプリケーションを開発しているときに、このエラーを解決するには  
  
1. アプリケーションが応答していない状態にならないことを確認します。  
  
2. カーネル オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。  
  
3. アプリケーションの元のインスタンスを再起動します。  
  
4. コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。  
  
5. エラーが発生した状況を記録して、Microsoft 製品サポート サービスに電話でご連絡ください。  
  
## <a name="see-also"></a>関連項目

- [デバッガーの基本事項](/visualstudio/debugger/debugger-basics)
