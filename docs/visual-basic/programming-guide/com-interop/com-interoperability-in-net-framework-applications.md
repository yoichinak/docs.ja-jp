---
title: .NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interoperability, COM and .NET framework objects
- COM interop [Visual Basic]
- shared components
ms.assetid: f5a72143-c268-4dff-a019-974ad940e17d
ms.openlocfilehash: ceef4255321e208911a16db0227890bc6654b8c5
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244665"
---
# <a name="com-interoperability-in-net-framework-applications-visual-basic"></a>.NET Framework アプリケーションにおける COM 相互運用性 (Visual Basic)
同じアプリケーションで COM オブジェクトと .NET Framework オブジェクトを使用する場合は、メモリ内のオブジェクトの存在の違いに対処する必要があります。 .NET Framework のオブジェクトは、マネージ メモリにある、共通言語ランタイムによって制御されるメモリ:、必要に応じて、ランタイムによって移動することがあります。 COM オブジェクトでは、アンマネージ メモリ内にあるし、別のメモリ位置に移動する必要はありません。 Visual Studio と[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]これらの相互作用を制御するためのツールのマネージし、アンマネージ コンポーネントを提供します。 マネージ コードの詳細については、[共通言語ランタイム](../../../standard/clr.md)を参照してください。  
  
 .NET アプリケーションで COM オブジェクトを使用するだけでなくすることも Visual Basic を使用して、COM 経由のアンマネージ コードからアクセスできるオブジェクトを開発するには  
  
 このページのリンクでは、COM と .NET Framework のオブジェクト間の相互作用の詳細を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [COM 相互運用](../../../visual-basic/programming-guide/com-interop/index.md)  
 COM オブジェクト、ActiveX コントロール、Win32 の Dll、管理対象のオブジェクト、および COM オブジェクトの継承をなど、Visual Basic における COM 相互運用性を説明するトピックへのリンクを提供します。  
  
 [COM 相互運用ラッパー エラー](/cpp/misc/com-interop-wrapper-error)  
 プロジェクト システムは、特定のコンポーネントの COM 相互運用ラッパーを作成できない場合の結果とオプションについて説明します。  
  
 [アンマネージ コードとの相互運用](../../../framework/interop/index.md)  
 簡単な説明、マネージとアンマネージ コード間の相互作用の問題の一部と、詳細情報へのリンクを示します。  
  
 [COM ラッパー](../../../framework/interop/com-wrappers.md)  
 マネージ コードから COM メソッドを呼び出すには、ランタイム呼び出し可能ラッパーを .NET オブジェクトのメソッドを呼び出す COM クライアントを許可する COM 呼び出し可能ラッパーについて説明します。  
  
 [高度な COM 相互運用性](../../../framework/interop/index.md)  
 ラッパー、例外、継承、スレッド処理、イベント、変換、およびマーシャ リングに対して COM 相互運用性を説明するトピックへのリンクを提供します。  
  
 [Tlbimp.exe (タイプ ライブラリ インポーター)](../../../framework/tools/tlbimp-exe-type-library-importer.md)  
 共通言語ランタイム アセンブリで等価な定義に COM タイプ ライブラリ内で見つかった種類の定義の変換に使用できるツールについて説明します。
