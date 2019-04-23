---
title: -win32manifest (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: 15fe62457ed11ffcd08a1db3aa8be57080f22869
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59300799"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
プロジェクトのポータブル実行可能 (PE) ファイルに埋め込まれる、ユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。  
  
## <a name="syntax"></a>構文  
  
```  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`fileName`|カスタム マニフェスト ファイルのパス。|  
  
## <a name="remarks"></a>Remarks  
 既定では、Visual Basic コンパイラは asInvoker の要求実行レベルを指定するアプリケーション マニフェストを埋め込みます。 実行可能ファイルが組み込まれている、通常は bin \debug または bin \release フォルダー Visual Studio を使用すると、同じフォルダーにマニフェストを作成します。 HighestAvailable または requireAdministrator の要求実行レベルを指定する例については、カスタム マニフェストを指定する場合は、ファイルの名前を指定するこのオプションを使用します。  
  
> [!NOTE]
>  このオプションと[-win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md)オプションは相互に排他的です。 同じコマンド行で両方のオプションを使用しようとする場合は、ビルド エラーが表示されます。  
  
 アプリケーション マニフェストを持たないアプリケーションは、要求実行レベルを指定した場合、Windows Vista のユーザー アカウント制御機能によって、ファイルまたはレジストリの仮想化の対象となります。 仮想化について詳しくは、「[Windows Vista の ClickOnce 配置](/visualstudio/deployment/clickonce-deployment-on-windows-vista)」を参照してください。  
  
 アプリケーションは、次の条件のいずれかが true の場合、仮想化されます。  
  
1. 使用する、`-nowin32manifest`オプションを渡さないように後のビルド手順で、または Windows リソース (.res) ファイルの一部としてマニフェストを使用して、`-win32resource`オプション。  
  
2. 要求実行レベルが指定されていないカスタム マニフェストを提供している。  
  
 Visual Studio は、既定の .manifest ファイルを作成し、それを実行可能ファイルと一緒にデバッグ ディレクトリとリリース ディレクトリに保存します。 表示したり、クリックして既定のアプリケーション マニフェスト ファイルを編集**UAC 設定の表示**上、**アプリケーション**プロジェクト デザイナー タブ。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
 行うことができます、アプリケーション マニフェストまたはカスタムのビルド後の手順として、Win32 リソース ファイルの一部としてを使用して、`-nowin32manifest`オプション。 アプリケーションを Windows Vista でファイルまたはレジストリの仮想化の対象にする場合は、これと同じオプションを使用します。 これにより、コンパイラからの作成と、PE ファイルの既定のマニフェストを埋め込むことができなくなります。  
  
## <a name="example"></a>例  
 次の例では、Visual Basic コンパイラが PE に挿入される既定のマニフェストを示しています。  
  
> [!NOTE]
>  コンパイラは、XML マニフェストに標準のアプリケーション名 MyApplication.app を挿入します。 これは、アプリケーションを Windows Server 2003 Service Pack 3 で実行できるようにするための回避策です。  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
