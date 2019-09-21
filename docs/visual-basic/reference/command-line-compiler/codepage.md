---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 3a5974a910303f847679f18c23e00cfaa00caa2c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962612"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`id`|必須。 コンパイラは、によって指定さ`id`れたコードページを使用して、ソースファイルのエンコーディングを解釈します。|  
  
## <a name="remarks"></a>Remarks  
 特定のエンコーディングを使用して保存されたソース`-codepage`コードをコンパイルするには、を使用して、使用するコードページを指定します。 オプション`-codepage`は、コンパイル時にすべてのソースコードファイルに適用されます。 詳細については、「 [.NET Framework の文字エンコード](../../../standard/base-types/character-encoding.md)」を参照してください。  
  
 ソースコードファイルが現在の ANSI コードページ、Unicode、または utf-8 を使用して署名されている場合、このオプションは必要ありません。`-codepage` Visual Studio では、ユーザーが **[エンコード]** ダイアログボックスで別のエンコードを指定しない限り、既定では、すべてのソースコードファイルが現在の ANSI コードページと共に保存されます。 Visual Studio では、 **[エンコード]** ダイアログボックスを使用して、別のコードページを使用して保存されたソースコードファイルを開きます。  
  
> [!NOTE]
> この`-codepage`オプションは、Visual Studio 開発環境内からは使用できません。コマンドラインからコンパイルする場合にのみ使用できます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
