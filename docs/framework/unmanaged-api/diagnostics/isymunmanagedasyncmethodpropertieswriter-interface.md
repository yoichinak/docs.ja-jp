---
title: ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス
ms.date: 03/30/2017
ms.assetid: caa71820-8058-4b6a-93a2-25ee757d92d3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82fcddd7a3f89a92cc79285930b30342333fbec2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112399"
---
# <a name="isymunmanagedasyncmethodpropertieswriter-interface"></a>ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス
各メソッドのシンボルのオプションの非同期メソッドの情報を定義することができます。 開かれているメソッド; で常に使用します。つまり、呼び出しの間で、 [OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)と[CloseMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)します。  
  
## <a name="syntax"></a>構文  
  
```idl  
[object,uuid(FC073774-1739-4232-BD56-A027294BEC15),pointer_default(unique)]interface ISymUnmanagedAsyncMethodPropertiesWriter : IUnknown  
```  
  
## <a name="methods"></a>メソッド  
 このインターフェイスには、次のメソッドが含まれています。  
  
|メソッド|説明|  
|------------|-----------------|  
|[DefineAsyncStepInfo メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-defineasyncstepinfo-method.md)|非同期のグループを定義、現在のメソッドでの操作を待機します。<br /><br /> 各 yield オフセットでは、潜在的な yield を識別する、await の戻り命令と一致します。 各`breakpointMethod` / `breakpointOffset`ペアを識別、非同期操作が再開されます。 別のメソッドである可能性があります。|  
|[DefineCatchHandlerILOffSet メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definecatchhandleriloffset-method.md)|IL オフセットの非同期メソッドをラップする catch のコンパイラによって生成されたハンドラーを設定します。<br /><br /> 生成された catch の IL オフセットは、ユーザー コード メソッドが発生する場合でも、非ユーザー コードの場合と同様に、catch を処理するために、デバッガーによって使用されます。 具体的への応答で使用される、 **CatchHandlerFound**例外イベント。|  
|[DefineKickoffMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-definekickoffmethod-method.md)|非同期操作を開始する開始メソッドを設定します。|  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>関連項目

- [シンボル ストア診断インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
