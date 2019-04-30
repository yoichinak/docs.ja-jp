---
title: '方法: .NET Framework 3.0 がインストールされているかどうかを確認する'
ms.date: 03/30/2017
helpviewer_keywords:
- WinFX Runtime user-agent string
- presence of WPT [WPF], detecting
- detecting WPF presence [WPF]
ms.assetid: 7f71d652-1749-4379-945a-aa2e3994cb43
ms.openlocfilehash: 27f856b895f48dc2365a1721dbc90294269899c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947824"
---
# <a name="how-to-detect-whether-the-net-framework-30-is-installed"></a>方法: .NET Framework 3.0 がインストールされているかどうかを確認する
管理者がシステム上の Microsoft .NET Framework アプリケーションを展開できる前にまず、.NET Framework ランタイムが存在するを確認する必要があります。 このトピックでは、HTML または JavaScript で記述されたスクリプトを提供します。 管理者は、.NET Framework が、システム上に存在するかどうかを使用できます。  
  
> [!NOTE]
>  配置、および Microsoft .NET Framework の検出が、説明を参照してインストールする方法についての詳細、[を展開する Microsoft .NET Framework バージョン 3.0](https://go.microsoft.com/fwlink/?LinkId=96739)します。  
  
<a name="content_expiration"></a>   
## <a name="detect-the-net-clr-user-agent-string"></a>".NET CLR"のユーザー エージェント文字列を検出します。  
 .NET Framework がインストールされている場合、MSI は、".NET CLR"とバージョン番号を UserAgent 文字列に追加します。 次の例では、単純な HTML ページに埋め込まれたスクリプトを示します。 スクリプトでは、.NET Framework がインストールされているし、検索の結果のステータス メッセージが表示されるかどうかを判断する UserAgent 文字列を検索します。  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.0</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.0.04425.00";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.0: "   
          + dotNETRuntimeVersion  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.0."  
      }  
      result.innerText += "\n\nThis machine's userAgent string is: " +   
        navigator.userAgent + ".";  
    }  
  
    //  
    // Retrieve the version from the user agent string and   
    // compare with the specified version.  
    //  
    function HasRuntimeVersion(versionToCheck)  
    {  
      var userAgentString =   
        navigator.userAgent.match(/.NET CLR [0-9.]+/g);  
  
      if (userAgentString != null)  
      {  
        var i;  
  
        for (i = 0; i < userAgentString.length; ++i)  
        {  
          if (CompareVersions(GetVersion(versionToCheck),   
            GetVersion(userAgentString[i])) <= 0)  
            return true;  
        }  
      }  
  
      return false;  
    }  
  
    //  
    // Extract the numeric part of the version string.  
    //  
    function GetVersion(versionString)  
    {  
      var numericString =   
        versionString.match(/([0-9]+)\.([0-9]+)\.([0-9]+)/i);  
      return numericString.slice(1);  
    }  
  
    //  
    // Compare the 2 version strings by converting them to numeric format.  
    //  
    function CompareVersions(version1, version2)  
    {  
      for (i = 0; i < version1.length; ++i)  
      {  
        var number1 = new Number(version1[i]);  
        var number2 = new Number(version2[i]);  
  
        if (number1 < number2)  
          return -1;  
  
        if (number1 > number2)  
          return 1;  
      }  
  
      return 0;  
    }  
  
    -->  
    </SCRIPT>  
  </HEAD>  
  
  <BODY>  
    <div id="result" />  
  </BODY>  
</HTML>  
```  
  
 ".NET CLR"バージョンの検索が成功した場合は、次のようなステータス メッセージが表示されます。  
  
 `This machine has the correct version of the .NET Framework 3.0: 3.0.04425.00`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727; .NET CLR 3.0.04425.00).`  
  
 それ以外の場合、次のようなステータス メッセージが表示されます。  
  
 `This machine does not have correct version of the .NET Framework 3.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.1; .NET CLR 1.1.4322; InfoPath.1; .NET CLR 2.0.50727).`
