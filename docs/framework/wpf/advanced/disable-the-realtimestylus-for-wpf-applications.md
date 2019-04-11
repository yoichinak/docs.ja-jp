---
title: WPF アプリケーションのリアルタイムなスタイラス入力を無効にする
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: e44b71ac5af64ab3a6cb008db71e5a8881592e91
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59124684"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>WPF アプリケーションのリアルタイムなスタイラス入力を無効にする
Windows Presentation Foundation (WPF) Windows 7 のタッチ入力を処理するためのサポートが組み込まれています。サポートがタブレット プラットフォームのリアルタイム スタイラス入力をそのまま<xref:System.Windows.UIElement.OnStylusDown%2A>、 <xref:System.Windows.UIElement.OnStylusUp%2A>、および<xref:System.Windows.UIElement.OnStylusMove%2A>イベント。 また、Windows 7 は、WM_TOUCH の Win32 ウィンドウ メッセージとしてマルチ タッチ入力を提供します。 これら 2 つの Api は、同じ HWND で相互に排他的です。 有効にするタッチでは、WM_TOUCH メッセージを無効にします。 tablet プラットフォーム (WPF アプリケーションの既定値) を使用して入力します。 その結果、WM_TOUCH を使用すると、WPF ウィンドウからタッチ メッセージを受信して、WPF での組み込みのスタイラスのサポートを無効にする必要があります。 これは、WM_TOUCH を使用するコンポーネントをホストする WPF ウィンドウなどのシナリオで適用します。  
  
 スタイラスからの入力をリッスンする WPF を無効にするには、WPF ウィンドウで追加された任意のタブレット サポートを削除します。  
  
## <a name="example"></a>例  
 次のサンプル コードでは、リフレクションを使用して既定のタブレット プラットフォームのサポートを削除する方法を示します。  
  
```  
public static void DisableWPFTabletSupport()  
{  
    // Get a collection of the tablet devices for this window.    
    TabletDeviceCollection devices = System.Windows.Input.Tablet.TabletDevices;  
  
    if (devices.Count > 0)  
    {     
        // Get the Type of InputManager.  
        Type inputManagerType = typeof(System.Windows.Input.InputManager);  
  
        // Call the StylusLogic method on the InputManager.Current instance.  
        object stylusLogic = inputManagerType.InvokeMember("StylusLogic",  
                    BindingFlags.GetProperty | BindingFlags.Instance | BindingFlags.NonPublic,  
                    null, InputManager.Current, null);  
  
        if (stylusLogic != null)  
        {  
            //  Get the type of the stylusLogic returned from the call to StylusLogic.  
            Type stylusLogicType = stylusLogic.GetType();  
  
            // Loop until there are no more devices to remove.  
            while (devices.Count > 0)  
            {  
                // Remove the first tablet device in the devices collection.  
                stylusLogicType.InvokeMember("OnTabletRemoved",  
                        BindingFlags.InvokeMethod | BindingFlags.Instance | BindingFlags.NonPublic,  
                        null, stylusLogic, new object[] { (uint)0 });  
            }                  
        }  
  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [スタイラスからの入力のインターセプト](intercepting-input-from-the-stylus.md)
