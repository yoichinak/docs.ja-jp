---
title: グローバル静的関数のプロファイル
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3ea65c06871d9762fa6daac229a568594b4c4479
ms.sourcegitcommit: 518e7634b86d3980ec7da5f8c308cc1054daedb7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/01/2019
ms.locfileid: "66457477"
---
# <a name="profiling-global-static-functions"></a>グローバル静的関数のプロファイル
このセクションでは、プロファイル API で使用されるアンマネージ API 関数について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET framework バージョン 1 のプロファイリング関数  
 [FunctionEnter 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 コントロールが関数に渡されることをプロファイラーに通知します。 .NET Framework 2.0 では、非推奨とされます。  
  
 [FunctionLeave 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 関数が呼び出し元に戻ることをプロファイラーに通知します。 .NET Framework 2.0 では、非推奨とされます。  
  
 [FunctionTailcall 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 現在実行中の関数が別の関数の末尾呼び出しを実行しようとすることをプロファイラーに通知します。 .NET Framework 2.0 では、非推奨とされます。  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET framework バージョン 2 のプロファイリング関数  
 [FunctionIDMapper 関数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 使用される代替 ID に、関数の指定した id 再割り当てされることをプロファイラーに通知、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)、および[FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)その関数のコールバック。 プロファイラーがその関数のコールバックを受信するかどうかを指定するができます。  
  
 [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 コントロールは、関数に渡されると、フレームと関数の引数はスタックに関する情報を提供をプロファイラーに通知します。 .NET Framework 4 では、非推奨とされます。  
  
 [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 プロファイラーに通知関数が呼び出し元に戻るには、し、スタック フレームと関数の戻り値に関する情報を提供します。 .NET Framework 4 では、非推奨とされます。  
  
 [FunctionTailcall2 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 現在実行中の関数が別の関数の末尾呼び出しを実行しようし、スタック フレームに関する情報を提供しますをプロファイラーに通知します。 .NET Framework 4 では、非推奨とされます。  
  
 [StackSnapshotCallback 関数](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 によって開始されるスタック ウォーク中にスタックの各マネージ フレームとフレームの非管理対象の各実行に関する情報を使用してプロファイラーを提供、 [icorprofilerinfo 2::dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)メソッド。  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET framework バージョン 4 のプロファイル関数  
 [FunctionIDMapper2 関数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 使用される代替 ID に、関数の指定した id 再割り当てされることをプロファイラーに通知、 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)、 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)、および[FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)、または[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)、 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)、および[FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)その関数のコールバック。 プロファイラーのコールバック関数を受信するかどうかを指定できます。  
  
 `FunctionIDMapper2` 拡張、 [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)関数と、`clientData`パラメーターで、プロファイラーを使用してランタイム間であいまいさを解消します。  
  
 [FunctionEnter3 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 コントロールが関数に渡されることをプロファイラーに通知します。  
  
 [FunctionEnter3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 コントロールが、関数に渡されることをプロファイラーに通知しに渡すことができるハンドルを提供します[icorprofilerinfo 3::getfunctionenter3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)スタック フレームと関数の引数を取得します。  
  
 [FunctionLeave3 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 コントロールが関数から返されることをプロファイラーに通知します。  
  
 [FunctionLeave3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 コントロールが、関数から返されることをプロファイラーに通知しに渡すことができるハンドルを提供します[icorprofilerinfo 3::getfunctionleave3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)スタック フレームおよび戻り値を取得します。  
  
 [FunctionTailcall3 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 現在実行中の関数が別の関数の末尾呼び出しを実行しようとすることをプロファイラーに通知します。  
  
 [FunctionTailcall3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 現在実行中の関数が別の関数の末尾呼び出しを実行しようとしているプロファイラーに通知しに渡すことができるハンドルを提供します[icorprofilerinfo 3::getfunctiontailcall3info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)スタック フレームを取得します。  
  
## <a name="related-sections"></a>関連項目  
 [プロファイルの概要](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
