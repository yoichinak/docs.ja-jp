---
title: CorpubPublish コクラス
ms.date: 03/30/2017
api_name:
- CorpubPublish Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorpubPublish
helpviewer_keywords:
- CorpubPublish coclass [.NET Framework debugging]
ms.assetid: 191015da-f54a-4bac-a28a-1de7ab3c3428
topic_type:
- apiref
ms.openlocfilehash: 89af99fab1f1265701e0dbfe74a46000cb3bfaa6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132146"
---
# <a name="corpubpublish-coclass"></a>CorpubPublish コクラス
アプリケーション ドメインとプロセスに関する情報を発行するためのインターフェイスを提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
coclass CorpubPublish {  
    [default] interface ICorPublish;  
    interface           ICorPublishProcess;  
    interface           ICorPublishAppDomain;  
    interface           ICorPublishProcessEnum;  
    interface           ICorPublishAppDomainEnum;  
};  
```  
  
## <a name="interfaces"></a>インターフェイス  
  
|Interface|説明|  
|---------------|-----------------|  
|[ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|プロセスおよびプロセス内のアプリケーションドメインに関する情報を公開するためのメソッドを提供します。|  
|[ICorPublishAppDomain インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|プロセス内のアプリケーションドメインに関する情報を表し、提供します。|  
|[ICorPublishAppDomainEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|プロセス内に現在存在するアプリケーションドメインのコレクションを走査するメソッドを提供します。|  
|[ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|コンピューター上で実行されているプロセスを表します。|  
|[ICorPublishProcessEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|コンピューター上で実行されているプロセスのコレクションを走査するメソッドを提供します。|  
  
## <a name="remarks"></a>Remarks  
 一般的な発行シナリオでは、開発者がアプリケーションドメイン内のコンピューターで実行されているマネージコードをデバッグする必要があります。 ホスト環境で、プロセス内で複数のアプリケーションドメインが実行されている可能性があります。 開発者は、コンピューター上で実行されているすべてのプロセスを一覧表示し、特定のプロセスを選択するために、グラフィカルユーザーインターフェイスまたはその他の方法を使用したいと考えています。 この一覧には、マネージコードを実行しているプロセス内のすべてのアプリケーションドメインが含まれている必要があります。 開発者は、特定のアプリケーションドメインを特定し、そのドメインにデバッガーをアタッチできます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorPub .idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
