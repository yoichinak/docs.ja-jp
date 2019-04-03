---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58819178"
---
# <a name="-filealign"></a>-filealign
出力ファイルでセクションをアラインするサイズを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>引数  
 `number`  
 必須。 出力ファイルのセクションの配置を指定する値。 有効値は 512、1024、2048、4096、および 8192 です。 これらの値はバイト単位です。  
  
## <a name="remarks"></a>Remarks  
 使用することができます、`-filealign`出力ファイル内のセクションのアラインメントを指定するオプション。 セクションは、コードまたはデータを含むポータブル実行可能ファイル (PE) ファイルの連続したメモリのブロックです。 `-filealign`オプションを使用して、非標準の配置を使用してアプリケーションをコンパイルできます。 ほとんどの開発者は、このオプションを使用する必要はありません。  
  
 各セクションは整列の倍数である境界、`-filealign`値。 固定の既定値はありません。 場合`-filealign`が指定されていない、コンパイラがコンパイル時に、既定値を選択します。  
  
 セクションのサイズを指定すると、出力ファイルのサイズを変更できます。 セクションのサイズ変更は、比較的小さなデバイスで実行されるプログラムに対して有効な場合があります。  
  
> [!NOTE]
>  `-filealign`オプションは、Visual Studio 開発環境内からは使用できません。 コマンドラインからコンパイルする場合にのみ使用可能なです。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
