---
title: '方法: .NET Framework 3.5 がインストールされているかどうかを検出します。'
ms.date: 03/30/2017
helpviewer_keywords:
- verifying whether.NET Framework 3.5 is installed [WPF]
- detecting .NET Framework 3.5 installation [WPF]
- detecting whether.NET Framework 3.5 is installed [WPF]
- determining whether.NET Framework 3.5 is installed [WPF]
ms.assetid: 8556a9d2-1eb8-48ef-919c-5baf22a2a9a2
ms.openlocfilehash: 2f3e3077f78aed90f4e213d61267131019664fdb
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378766"
---
# <a name="how-to-detect-whether-the-net-framework-35-is-installed"></a>方法: .NET Framework 3.5 がインストールされているかどうかを検出します。
管理者が対象とするシステム上の Windows Presentation Foundation (WPF) アプリケーションを展開する前に、 [!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]、ことを確認する必要があります最初、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]ランタイムが存在します。 このトピックで記述されたスクリプトは、管理者は、判断に使用できる HTML または JavaScript でかどうか、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]は、システムに存在します。  
  
> [!NOTE]
>  詳細なインストール、展開、および検出については、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]を参照してください[開発者向けの .NET Framework のインストール](../../install/guide-for-developers.md)します。  
  
## <a name="example"></a>例  
 ときに、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]がインストールされている場合、MSI を追加します".NET CLR"とバージョン番号 UserAgent 文字列。 次の例では、単純な HTML ページに埋め込まれたスクリプトを示します。 スクリプトを決定する UserAgent 文字列を検索するかどうか、[!INCLUDE[net_v35_short](../../../../includes/net-v35-short-md.md)]がインストールされているし、検索の結果にステータス メッセージが表示されます。  
  
> [!NOTE]
>  このスクリプトは、Internet Explorer 用に設計されています。 その他のブラウザーは、UserAgent 文字列の .NET CLR の情報を含まない場合があります。  
  
```  
<HTML>  
  <HEAD>  
    <TITLE>Test for the .NET Framework 3.5</TITLE>  
    <META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=utf-8" />  
    <SCRIPT LANGUAGE="JavaScript">  
    <!--  
    var dotNETRuntimeVersion = "3.5.0.0";  
  
    function window::onload()  
    {  
      if (HasRuntimeVersion(dotNETRuntimeVersion))  
      {  
        result.innerText =   
          "This machine has the correct version of the .NET Framework 3.5."  
      }   
      else  
      {  
        result.innerText =   
          "This machine does not have the correct version of the .NET Framework 3.5." +  
          " The required version is v" + dotNETRuntimeVersion + ".";  
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
  
 `This machine has the correct version of the .NET Framework 3.5.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; .NET CLR 3.5.20726; MS-RTC LM 8).`  
  
 それ以外の場合、次のようなステータス メッセージが表示されます。  
  
 `This machine does not have the correct version of the .NET Framework 3.5. The required version is v3.5.0.0.`  
  
 `This machine's userAgent string is: Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 6.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 3.0.590; MS-RTC LM 8).`  
  
## <a name="see-also"></a>関連項目
- [.NET Framework 3.0 がインストールされているかどうかを確認する](how-to-detect-whether-the-net-framework-3-0-is-installed.md)
