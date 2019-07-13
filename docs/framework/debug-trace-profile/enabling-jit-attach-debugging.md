---
title: JIT アタッチ デバッグの有効化
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 005395beabd956767b59e0cebd563fe883f6fe53
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489798"
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
  
 .NET Framework 4 では、前に、.NET Framework には、ネイティブおよびマネージ デバッガーの動作を制御する別々 のレジストリ キーが用意されています。 以降、.NET Framework 4 では、コントロールが 1 つのレジストリ キーの下で統合します。Hkey_local_machine \software\microsoft\windows \current Version\AeDebug します。 このキーに設定できる値により、デバッガーを呼び出すかどうか、呼び出す場合は、ユーザーの操作を必要とするダイアログ ボックスによって呼び出すかどうかが決まります。 このレジストリ キーの設定方法の詳細については、次を参照してください。[自動デバッグ構成](https://go.microsoft.com/fwlink/?LinkId=181767)します。  
  
## <a name="see-also"></a>関連項目

- [デバッグ、トレース、およびプロファイリング](../../../docs/framework/debug-trace-profile/index.md)
- [イメージのデバッグの簡略化](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)
