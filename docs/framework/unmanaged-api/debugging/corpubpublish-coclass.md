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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d1ca8ea9d00de8a07c67977cf108c50268802e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739361"
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
|[ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)|これらのプロセスでプロセスとアプリケーション ドメインに関する情報を公開するためのメソッドを提供します。|  
|[ICorPublishAppDomain インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)|表していると、プロセス内のアプリケーション ドメインに関する情報を提供します。|  
|[ICorPublishAppDomainEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)|現在、プロセス内に存在するアプリケーション ドメインのコレクションを走査するメソッドを提供します。|  
|[ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)|コンピューターで実行されているプロセスを表します。|  
|[ICorPublishProcessEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)|コンピューターで実行されているプロセスのコレクションを走査するメソッドを提供します。|  
  
## <a name="remarks"></a>Remarks  
 発行の一般的なシナリオでは、開発者は、アプリケーション ドメイン内のコンピューターで実行されているマネージ コードをデバッグする必要があります。 ホスティング環境では、プロセス内で 1 つ以上のアプリケーション ドメインが実行されている可能性があります。 開発者は、グラフィカル ユーザー インターフェイスまたはその他の手段を使用して、すべてのコンピューターで実行されているプロセスの一覧を表示して、特定のプロセスを選択したいです。 一覧には、すべてのマネージ コードを実行しているプロセス内でアプリケーション ドメインを含める必要があります。 開発者は特定のアプリケーション ドメインを識別し、そのドメインにデバッガーをアタッチします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorPub.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:**  [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
