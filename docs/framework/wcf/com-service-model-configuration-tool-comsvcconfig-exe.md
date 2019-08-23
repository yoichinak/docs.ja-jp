---
title: COM+ サービス モデル構成ツール (ComSvcConfig.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM+ integration
- WCF, COM+ integration
ms.assetid: 7717c6c2-85fc-418b-a8ed-bad8e61cec5c
ms.openlocfilehash: 89462d05b9da7fc63bda58955517bfa9f0c50ab9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964196"
---
# <a name="com-service-model-configuration-tool-comsvcconfigexe"></a>COM+ サービス モデル構成ツール (ComSvcConfig.exe)
COM+ サービス モデル構成コマンド ライン ツール (ComSvcConfig.exe) を使用すると、COM+ インターフェイスを Web サービスとして公開するように構成できます。  
  
## <a name="syntax"></a>構文  
  
```  
ComSvcConfig.exe /install | /uninstall | /list [/application:<ApplicationID | ApplicationName>] [/contract:<ClassID | ProgID | *,InterfaceID | InterfaceName | *>] [/hosting:<complus | was>] [/webSite:<WebsiteName>] [/webDirectory:<WebDirectoryName>] [/mex] [/id] [/nologo] [/verbose] [/help] [/partial]  
```  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> ComSvcConfig.exe を使用するには、ローカル コンピューターの管理者である必要があります。  
  
 ツールは次の場所にあります。  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows Communication Foundation\  
  
 Comsvcconfig.exe の詳細については、「 [」を参照してください。COM + サービスモデル構成ツール](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)を使用します。  
  
 次の表は、ComSvcConfig.exe で使用できるモードを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|`install`|サービス モデル統合に COM+ インターフェイスの構成をインストールします。<br /><br /> 短縮形 : `/i`。|  
|`uninstall`|サービス モデル統合から COM+ インターフェイスの構成をアンインストールします。<br /><br /> 短縮形 : `/u`。|  
|`list`|サービス モデル統合に構成されるインターフェイスを持つ COM+ アプリケーションとコンポーネントの情報を一覧表示します。<br /><br /> 短縮形 : `/l`。|  
  
 次の表は、ComSvcConfig.exe で使用できるフラグを示します。  
  
|オプション|説明|  
|------------|-----------------|  
|`/application:`&#124; ApplicationID \<ApplicationName\>|構成する COM+ アプリケーションを指定します。<br /><br /> 短縮形 : `/a`。|  
|`/contract:`&#124; &#124; &#124; ClassID ProgID&#124; *、interfaceid* InterfaceName \< \*    \*\>|サービスのコントラクトとして構成される COM+ コンポーネントとインターフェイスを指定します。<br /><br /> 短縮形 : `/c`。<br /><br /> ワイルドカード文字 (\*) は、コンポーネントとインターフェイスの名前を指定するときに使用できますが、意図していないインターフェイスを公開する可能性があるため、使用しないことをお勧めします。|  
|`/hosting:`&#124; complus \<は  \>|COM+ ホスト モードと Web ホスト モードのどちらを使用するかを指定します。<br /><br /> 短縮形 : `/h`。<br /><br /> COM+ ホスト モードを使用するには、COM + アプリケーションの明示的なアクティブ化が必要です。 Web ホスト モードを使用すると、COM+ アプリケーションを必要なときに自動的にアクティブ化できます。 COM+ アプリケーションがライブラリ アプリケーションの場合は、インターネット インフォメーション サービス (IIS) のプロセスで実行します。 COM+ アプリケーションがサーバー アプリケーションの場合は、Dllhost.exe のプロセスで実行します。|  
|`/webSite:`\< *WebsiteName*\>|Web ホスト モードを使用する場合は、ホストする Web サイトを指定します (`/hosting` フラグを参照)。<br /><br /> 短縮形 : `/w`。<br /><br /> Web サイトを指定しない場合は、既定の Web サイトが使用されます。|  
|`/webDirectory:`\< *WebDirectoryName*\>|Web ホストを使用する場合は、ホストする仮想ディレクトリを指定します (`/hosting` フラグを参照)。<br /><br /> 短縮形 : `/d`。|  
|`/mex`|サービスからコントラクト定義を取得するクライアントをサポートするには、既定のサービス構成に Metadata Exchange (MEX) サービス エンドポイントを追加します。<br /><br /> 短縮形 : `/x`。|  
|`/id`|アプリケーション、コンポーネント、およびインターフェイス情報を ID として表示します。<br /><br /> 短縮形 : `/k`。|  
|`/nologo`|ComSvcConfig.exe がロゴを表示しないようにします。<br /><br /> 短縮形 : `/n`。|  
|`/verbose`|発生するエラーに加えて、すべての警告または情報テキストを出力します。<br /><br /> 短縮形 : `/v`。|  
|`/help`|使用方法を示すメッセージを表示します。<br /><br /> 短縮形 : `/?`。|  
|`/partial`|指定されたインターフェイスが、公開できる 1 つ以上のメソッド署名を含む場合にサービス構成を生成します。 サービスの初期化時に、互換性のあるメソッドはサービス コントラクトで操作として表示され、互換性のないメソッドはサービス コントラクトから除外されます。<br /><br /> このフラグが指定されていない場合は、指定されたインターフェイスが互換性のないメソッドを 1 つ以上含むとツールはサービス構成を生成しません。|  
  
## <a name="examples"></a>使用例  
  
### <a name="description"></a>説明  
 次の例は、COM+ ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.IFinancial` インターフェイスを追加します。 発生するエラーに加えて、すべての警告が出力されます。  
  
### <a name="code"></a>コード  
  
```  
ComSvcConfig.exe /install /application:OnlineStore /contract:ItemOrders.Financial,IFinances /hosting:complus /verbose  
```  
  
### <a name="description"></a>説明  
 次の例は、Web ホスト モードを使用する Web サービスとして公開されるインターフェイスのセットに (OnlineWarehouse COM+ アプリケーションの) `IStockLevels` コンポーネントの `ItemInventory.Warehouse` インターフェイスを追加します。 Web サービスは、IIS の OnlineWarehouse 仮想ディレクトリで Web ホストされます。  
  
### <a name="code"></a>コード  
  
```  
ComSvcConfig.exe /install /application:OnlineWarehouse /contract:ItemInventory.Warehouse,IStockLevels /hosting:was /webDirectory:root/OnlineWarehouse  
```  
  
### <a name="description"></a>説明  
 次の例は、Web サービスとして公開されるインターフェイスのセットから (OnlineStore COM+ アプリケーションの) `IFinances` コンポーネントの `ItemOrders.Financial` インターフェイスを削除します。  
  
### <a name="code"></a>コード  
  
```  
ComSvcConfig.exe /uninstall /application:OnlineStore /interface:ItemOrders.Financial,IFinances /hosting:complus  
```  
  
### <a name="description"></a>説明  
 次の例は、ローカル マシン上の OnlineStore COM+ アプリケーションの現在公開されている COM+ ホスト インターフェイスを、対応するアドレスやバインディングの詳細と共に一覧表示します。  
  
### <a name="code"></a>コード  
  
```  
ComSvcConfig.exe /list /application:OnlineStore /hosting:complus  
```  
  
## <a name="see-also"></a>関連項目

- [方法: COM + サービスモデル構成ツールの使用](../../../docs/framework/wcf/feature-details/how-to-use-the-com-service-model-configuration-tool.md)
