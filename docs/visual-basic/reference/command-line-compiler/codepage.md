---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: e4cdc27ab021fe055f157b78946538f2b76870e1
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002362"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>引数  
  
|項目|定義|  
|---|---|  
|`id`|必須。 コンパイラは、`id` で指定されたコードページを使用して、ソースファイルのエンコーディングを解釈します。|  
  
## <a name="remarks"></a>コメント  
 特定のエンコーディングを使用して保存されたソースコードをコンパイルするには、`-codepage` を使用して、使用するコードページを指定します。 @No__t-0 オプションは、コンパイル時にすべてのソースコードファイルに適用されます。 詳細については、「 [.NET Framework の文字エンコード](../../../standard/base-types/character-encoding.md)」を参照してください。  
  
 現在の ANSI コードページ、Unicode、または UTF-8 を使用してソースコードファイルが保存されている場合、`-codepage` オプションは必要ありません。 Visual Studio では、ユーザーが **[エンコード]** ダイアログボックスで別のエンコードを指定しない限り、既定では、すべてのソースコードファイルが現在の ANSI コードページと共に保存されます。 Visual Studio では、 **[エンコード]** ダイアログボックスを使用して、別のコードページを使用して保存されたソースコードファイルを開きます。  
  
> [!NOTE]
> @No__t-0 オプションは、Visual Studio 開発環境内からは使用できません。これは、コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
