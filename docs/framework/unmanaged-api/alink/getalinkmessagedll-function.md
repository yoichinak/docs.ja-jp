---
title: GetALinkMessageDll 関数
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 323e53c45a26d5703548ebe9863978f6d3929f0b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787484"
---
# <a name="getalinkmessagedll-function"></a>GetALinkMessageDll 関数
メッセージ DLL を検索して読み込みます。 メッセージ DLL が見つからないか、または読み込むことができなかった場合は0を返します。 メッセージ DLL は、名前が言語 ID または現在のディレクトリ内のサブディレクトリにある必要があります。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a>必要条件  
 **ヘッダー:** alink  
  
 **ライブラリ**: alink  
  
## <a name="see-also"></a>関連項目

- [Al.exe (アセンブリ リンカー)](../../tools/al-exe-assembly-linker.md)
