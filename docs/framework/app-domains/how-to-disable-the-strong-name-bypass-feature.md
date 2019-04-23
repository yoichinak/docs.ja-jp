---
title: '方法: 厳密な名前のバイパス機能を無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86fc35ae20211bd32a21d60b7313074361aef671
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59296174"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>方法: 厳密な名前のバイパス機能を無効にする
.NET Framework Version 3.5 Service Pack 1 (SP1) 以降、アセンブリが完全信頼の <xref:System.AppDomain> オブジェクト (`MyComputer` ゾーンに既定の <xref:System.AppDomain> など) に読み込まれている場合は、厳密な名前の署名の検証が行われなくなりました。 これは厳密な名前のバイパス機能と呼ばれます。 完全に信頼された環境では、<xref:System.Security.Permissions.StrongNameIdentityPermission> に対する完全に信頼された署名済みアセンブリの要求は、その署名に関係なく、常に成功します。 ゾーンは完全に信頼されているため、唯一の制限として、アセンブリは完全に信頼されている必要があります。 このような状況では厳密な名前は決定要因ではないため、これを検証する理由はありません。 厳密な名前の署名の検証をバイパスすることで、パフォーマンスが大幅に向上します。  
  
 バイパス機能は、<xref:System.AppDomainSetup.ApplicationBase%2A> プロパティで指定されたディレクトリから完全信頼の <xref:System.AppDomain> に読み込まれ、遅延署名されていないすべての完全信頼アセンブリに適用されます。  
  
 レジストリ キー値を設定することで、コンピューターのすべてのアプリケーションに対するバイパス機能をオーバーライドできます。 アプリケーションの構成ファイルを使用すると、単一アプリケーションの設定をオーバーライドできます。 レジストリ キーを使用して無効にされているアプリケーションでは、個別にバイパス機能を元に戻すことはできません。  
  
 バイパス機能をオーバーライドすると、厳密な名前が正しいかどうかだけが検証されます。<xref:System.Security.Permissions.StrongNameIdentityPermission> に対するチェックは行われません。 特定の厳密な名前を確認するには、個別にチェックを実行する必要があります。  
  
> [!IMPORTANT]
>  厳密な名前の検証を強制する機能は、次の手順で説明するように、レジストリ キーに依存します。 アプリケーションが、該当のレジストリ キーへのアクセスについてアクセス制御リスト (ACL) アクセス許可を持っていないアカウントで実行されている場合、その設定は無効となります。 ACL アクセス許可を構成し、すべてのアセンブリ用に読み取ることができるようにキーを設定する必要があります。  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>すべてのアプリケーションに対して厳密な名前のバイパス機能を無効にするには  
  
-   32 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーの下に、値が 0 の `AllowStrongNameBypass` という名前のダブルワード エントリを作成します。  
  
-   64 ビット コンピューターでは、システム レジストリの HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework キーと HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework キーの下に、値が 0 の `AllowStrongNameBypass` という名前のダブルワード エントリを作成します。  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>単一のアプリケーションに対して厳密な名前のバイパス機能を無効にするには  
  
1. アプリケーションの構成ファイルを開くか、または作成します。  
  
     このファイルの詳細については、「[構成ファイルを使用してアプリを構成する方法](../../../docs/framework/configure-apps/index.md)」の「アプリケーション構成ファイル」を参照してください。  
  
2. 次のエントリを追加します。  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 アプリケーションのバイパス機能を元に戻すには、構成ファイル設定を削除するか、属性を "true" に設定します。  
  
> [!NOTE]
>  アプリケーションに対して厳密な名前のバイパス機能の有効/無効を切り替えることができるのは、コンピューターでバイパス機能が有効になっている場合だけです。 コンピューターでバイパス機能が無効になっている場合は、すべてのアプリケーションに対して厳密な名前が検証され、単一のアプリケーションに対する検証をバイパスすることはできません。  
  
## <a name="see-also"></a>関連項目

- [Sn.exe (厳密名ツール)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames> 要素](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [厳密な名前付きアセンブリの作成と使用](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
