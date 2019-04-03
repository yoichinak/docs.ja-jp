---
title: s_isDebuggerCheckDisabledForTestPurposes フィールド
ms.date: 03/30/2017
ms.technology: dotnet-wpf
topic_type:
- apiref
api_name:
- System.Windows.Diagnostics.VisualDiagnostics.s_isDebuggerCheckDisabledForTestPurposes
api_location:
- PresentationCore.dll
api_type:
- Assembly
ms.assetid: 9033a513-c255-4f31-b6d7-09b8d8c50e2d
ms.openlocfilehash: ab71ab6aa2b0ed454b86388ba369204a2131cca5
ms.sourcegitcommit: d938c39afb9216db377d0f0ecdaa53936a851059
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2019
ms.locfileid: "58634428"
---
# <a name="sisdebuggercheckdisabledfortestpurposes-field"></a>s_isDebuggerCheckDisabledForTestPurposes フィールド

このプライベート フィールドで、`System.Windows.Diagnostics.VisualDiagnostics`クラスは、アクティブなデバッガー、内部のチェックを実行するかどうかを判断する Visual Studio によって使用されます。

## <a name="syntax"></a>構文

```csharp
private static bool s_isDebuggerCheckDisabledForTestPurposes
```

> [!WARNING]
> Api、`System.Windows.Diagnostics.VisualDiagnostics`クラスは、アプリケーションがデバッガーで実行されている場合にのみ使用できます。 設定`s_isDebuggerCheckDisabledForTestPurposes`に`true`デバッガーの外部 Api にアクセスします。
>
> Microsoft はいかなる運用アプリケーションでこのフィールドの使用をサポートしていません。

## <a name="requirements"></a>必要条件

**名前空間:** <xref:System.Windows.Diagnostics>

**アセンブリ:** PresentationCore (presentationcore.dll 内)

**.NET framework のバージョン:** 4.6 以降で使用可能です。