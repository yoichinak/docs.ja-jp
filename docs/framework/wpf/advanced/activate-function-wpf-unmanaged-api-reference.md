---
title: Activate 関数 (WPF のアンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- Activate
api_location:
- PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
ms.openlocfilehash: ee231653815bd5ef75d58979034e3b3be9f5ba54
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480781"
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a>Activate 関数 (WPF のアンマネージ API リファレンス)

この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしているし、コードから直接使用するものではありません。

Windows Presentation Foundation (WPF) インフラストラクチャによって windows の管理に使用します。

## <a name="syntax"></a>構文

```cpp
void Activate(
    const ActivateParameters* pParameters,
    __deref_out_ecount(1) LPUNKNOWN* ppInner,
    );
```

## <a name="parameters"></a>パラメーター

`pParameters`\
ウィンドウのアクティブ化パラメーターへのポインター。

`ppInner`\
ポインターを格納している 1 つの要素のバッファーのアドレスへのポインター、<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>オブジェクト。

## <a name="requirements"></a>必要条件

**プラットフォーム:** 参照してください[.NET Framework システム要件](../../get-started/system-requirements.md)します。

**DLL:**

.NET framework 3.0 および 3.5。PresentationHostDLL.dll

.NET framework 4 以降では。PresentationHost_v0400.dll

**.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]

## <a name="see-also"></a>関連項目

- [WPF のアンマネージ API リファレンス](wpf-unmanaged-api-reference.md)
