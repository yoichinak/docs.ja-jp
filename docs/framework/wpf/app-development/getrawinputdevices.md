---
title: GetRawInputDevices
ms.date: 03/30/2017
helpviewer_keywords:
- raw input [WPF]
ms.assetid: c4d37ecd-065a-4d1c-9e6c-26804ae968ca
ms.openlocfilehash: 86910434e572bc19595d1664347f35d7a39eb75b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365101"
---
# <a name="getrawinputdevices"></a>GetRawInputDevices
PresentationHost.exe が、ホスト アプリケーションに必要な未加工入力デバイス (ヒューマン インターフェイス デバイス) を検出できるようにします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetRawInputDevices( [out] IEnumRAWINPUTDEVICE **ppEnum );  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppEnum`  
  
 [out]ポインター、 [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md)未加工入力デバイスを列挙するためです。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:  
  
 S_OK - [IEnumRAWINPUTDEVICE](ienumrawinputdevice.md) S_OK が返された場合のみ PresentationHost.exe によってに使用されます。  
  
 E_NOTIMPL  
  
## <a name="remarks"></a>Remarks  
 未加工入力デバイスは、キーボード、マウス、およびリモート コントロールのような比較的新しいデバイスを含む入力デバイスのセットです。  
  
 未加工の入力デバイスの一覧を取得すると、PresentationHost.exe は WM_INPUT 通知メッセージを受信するデバイスを登録します。  
  
## <a name="see-also"></a>関連項目
- [GetRawInputDeviceList](/windows/desktop/api/winuser/nf-winuser-getrawinputdevicelist)
- [FilterInputMessage](filterinputmessage.md)
