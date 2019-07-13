---
title: カスタム メッセージ フォーマッタ
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: af1596c65fc87a68bc3dc2ab5ab2d82133e0fed4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857975"
---
# <a name="custom-message-formatters"></a>カスタム メッセージ フォーマッタ
メッセージの内容は、XML 形式で表されることが多く、この形式は通常、アプリケーションにとって処理しやすい形式ではありません。 アプリケーションでは、オブジェクトのプロパティを取得および設定することによってオブジェクトを操作します。 Windows Communication Foundation (WCF) を使用して、*データ コントラクト*に変換する、<xref:System.ServiceModel.Channels.Message>オブジェクトに、オブジェクトをアプリケーションで簡単に処理します。 このプロセスは、シリアル化および逆シリアル化と呼ばれます。 これと同じ用語が、トランスポート層によって行われるメッセージ ワイヤ形式へのシリアル化とその形式からの逆シリアル化を説明するときに使用されますが、これは関連のないプロセスです。  
  
 データ コントラクトによって実現できないメッセージとオブジェクト間の特殊な変換を実装する必要がある場合、カスタム メッセージ フォーマッタを使用できます。 これを使用するには、クライアントまたはサービス上で特定のコントラクト操作の実行動作を変更または拡張します。  
  
## <a name="custom-message-formatters-on-the-client"></a>クライアントのカスタム メッセージ フォーマッタ  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> インターフェイスは、メッセージからオブジェクトへの変換およびオブジェクトからクライアント アプリケーション用のメッセージへの変換を制御するためのメソッドを定義します。  
  
 このインターフェイスを実装する必要があります。 まず、メッセージを逆シリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> メソッドをオーバーライドします。 このメソッドは、受信メッセージを受信した後でそのメッセージがクライアント操作にディスパッチされる前に呼び出されます。  
  
 次に、オブジェクトをシリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> メソッドをオーバーライドします。 このメソッドは、送信メッセージを送信する前に呼び出されます。  
  
 カスタム フォーマッタをサービス アプリケーションに挿入するには、操作の動作を使用して、<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> オブジェクトを <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> プロパティに割り当てます。 動作については、次を参照してください。[構成と、ランタイムの動作を拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)します。  
  
## <a name="custom-message-formatters-on-the-service"></a>サービスのカスタム メッセージ フォーマッタ  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> インターフェイスは、<xref:System.ServiceModel.Channels.Message> オブジェクトを操作用のパラメーターに変換し、これらのパラメーターをサービス アプリケーション用の <xref:System.ServiceModel.Channels.Message> オブジェクトに変換するためのメソッドを定義します。  
  
 このインターフェイスを実装する必要があります。 まず、メッセージを逆シリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> メソッドをオーバーライドします。 このメソッドは、受信メッセージを受信した後でそのメッセージがクライアント操作にディスパッチされる前に呼び出されます。  
  
 次に、オブジェクトをシリアル化するための <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> メソッドをオーバーライドします。 このメソッドは、送信メッセージを送信する前に呼び出されます。  
  
 カスタム フォーマッタをサービス アプリケーションに挿入するには、操作の動作を使用して、<xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> オブジェクトを <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> プロパティに割り当てます。 動作については、次を参照してください。[構成と、ランタイムの動作を拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [動作を使用したランタイムの構成と拡張](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
