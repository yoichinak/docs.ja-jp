---
title: リアルタイムスタイラスを無効にする
ms.date: 03/30/2017
ms.assetid: e0525309-5ede-4782-837d-dbf6e5554859
ms.openlocfilehash: c2500b494f76c85e4b23823a44a180d85d5092ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186077"
---
# <a name="disable-the-realtimestylus-for-wpf-applications"></a>WPF アプリケーションのリアルタイムなスタイラス入力を無効にする

Windows プレゼンテーションファンデーション (WPF) は、Windows 7 タッチ入力の処理のサポートを組み込まれています。 サポートは、タブレット プラットフォームのリアルタイムスタイラス入力 、 、<xref:System.Windows.UIElement.OnStylusDown%2A><xref:System.Windows.UIElement.OnStylusUp%2A>および<xref:System.Windows.UIElement.OnStylusMove%2A>イベントを介して提供されます。 Windows 7 では、ウィンドウ メッセージの Win32 WM_TOUCHマルチタッチ入力も提供されます。 これら 2 つの API は、同じ HWND 上で相互に排他的です。 タブレット プラットフォーム (WPF アプリケーションの既定値) を介してタッチ入力を有効にすると、WM_TOUCHメッセージが無効になります。 その結果、WM_TOUCHを使用して WPF ウィンドウからタッチ メッセージを受信するには、WPF で組み込みのスタイラス サポートを無効にする必要があります。 これは、WM_TOUCHを使用するコンポーネントをホストする WPF ウィンドウなどのシナリオに適用されます。  
  
 スタイラス入力をリッスンする WPF を無効にするには、WPF ウィンドウによって追加されたタブレット サポートを削除します。  
  
## <a name="example"></a>例  
 次のサンプル コードは、リフレクションを使用して既定のタブレット プラットフォーム サポートを削除する方法を示しています。  
  
```csharp  
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
