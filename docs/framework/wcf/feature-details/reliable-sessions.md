---
title: 信頼できるセッション
ms.date: 03/30/2017
f1_keywords:
- Windows Communication Foundation, sessions and instances
- WCF, sessions and instances
- sessions and instances [WCF]
helpviewer_keywords:
- instances [WCF]
- sessions [WCF]
ms.assetid: 143951b3-3aa0-4540-b4b7-d33e77e874a1
ms.openlocfilehash: 9a2cd06c4c5a73d9fb5c4c7f09632e10c3eb0d87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991160"
---
# <a name="reliable-sessions"></a>信頼できるセッション

このセクションでは、どのような Windows Communication Foundation (WCF) 信頼できるセッションが、用途も、方法およびと 1 つを使用するバインド構成をサポートしのポインターのベスト プラクティスについて説明します。 このセクションの重要なポイントと関連するトピックの詳細について、次の表にまとめます。

信頼できるセッションが WCF には、エンドポイント間で送信されるメッセージが SOAP またはトランスポート中継ぎ局を介して転送して、1 回のみと、必要に応じて、送信された順序で配信されることを確認する機能が用意されています。

で WCF アプリケーションを信頼できるセッションを使用するには、既定またはオプションとして、信頼できるセッションをサポートして WCF でのシステム提供バインディングのいずれかを使用するか、セッションをサポートする独自のカスタム バインドを作成します。

## <a name="in-this-section"></a>このセクションの内容

[信頼できるセッションの概要](../../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)信頼できるセッションの説明に、信頼できるセッションをサポートする各種のバインディングを使用する場合とそのしくみ。

[方法: Exchange のメッセージ内で、信頼できるセッション](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)構成に指定されたカスタム バインディングを使用して HTTP 経由で信頼できるセッションを作成する方法について説明します。

[方法: 信頼できるセッション内のメッセージをセキュリティで保護された](../../../../docs/framework/wcf/feature-details/how-to-secure-messages-within-reliable-sessions.md)信頼できるセッションをセキュリティで保護する方法について説明します。

[方法: HTTPS でカスタム信頼できるセッション バインドを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)HTTPS 経由で信頼できるセッションを作成する方法について説明します。

[信頼できるセッションのベスト プラクティス](../../../../docs/framework/wcf/feature-details/best-practices-for-reliable-sessions.md)の信頼できるセッションの使用に関連するベスト プラクティスについて説明します。

## <a name="reference"></a>参照

<xref:System.ServiceModel.ReliableSession>

## <a name="see-also"></a>関連項目

- [キューと信頼できるセッション](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
- [セッション、インスタンス化、およびコンカレンシー](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
