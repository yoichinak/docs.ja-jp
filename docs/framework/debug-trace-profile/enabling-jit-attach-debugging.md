---
title: JIT アタッチ デバッグの有効化
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052832"
---
# <a name="enabling-jit-attach-debugging"></a>JIT アタッチ デバッグの有効化
JIT アタッチ デバッグとは、エラーが発生したとき、または特定のメソッドまたは関数によってトリガーすることで、プロセスにデバッガーをアタッチすることを表すために使用される語句です。  
  
 JIT アタッチ デバッグは、次のエラー状態で使用されます。  
  
- 未処理の例外 (ネイティブ コードとマネージド コードの両方)。  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> メソッドまたは [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) 関数 (Windows 7 ファミリ)。  
  
- 実行時の致命的なエラー。  
  
 JIT アタッチ デバッグは、次のメソッドや関数への呼び出しによってもトリガーされます。  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> メソッド  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> メソッド  
  
- [DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) 関数 (Win32)。  
  
 .NET Framework 4 より前の .NET Framework では、ネイティブデバッガーとマネージデバッガーの動作を制御するために個別のレジストリキーが提供されていました。 .NET Framework 4 以降では、1つのレジストリキーの下にコントロールが統合されています。HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug. このキーに設定できる値により、デバッガーを呼び出すかどうか、呼び出す場合は、ユーザーの操作を必要とするダイアログ ボックスによって呼び出すかどうかが決まります。 このレジストリキーの設定の詳細については、「[自動デバッグの構成](https://go.microsoft.com/fwlink/?LinkId=181767)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [デバッグ、トレース、およびプロファイリング](index.md)
- [イメージのデバッグの簡略化](making-an-image-easier-to-debug.md)
