---
title: Fusion グローバル静的関数
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged global static functions [.NET Framework], fusion
- fusion global static functions [.NET Framework]
- global static functions [.NET Framework fusion]
ms.assetid: 229b2188-9168-4b44-a987-e1f515494688
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86cb59c0935c193a9865d5ace5fe11c96226d9e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697720"
---
# <a name="fusion-global-static-functions"></a>Fusion グローバル静的関数
このセクションでは、fusion API が使用されるアンマネージ グローバル静的関数について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ClearDownloadCache 関数](../../../../docs/framework/unmanaged-api/fusion/cleardownloadcache-function.md)  
 ダウンロードしたアセンブリのグローバル アセンブリ キャッシュをクリアします。  
  
 [CompareAssemblyIdentity 関数](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)  
 2 つのアセンブリ id と同じかどうかを比較します。  
  
 [CreateApplicationContext 関数](../../../../docs/framework/unmanaged-api/fusion/createapplicationcontext-function.md)  
 内部のみ。 (この関数は、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [CreateAssemblyCache 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblycache-function.md)  
 新しいポインターを取得します。 [IAssemblyCache](../../../../docs/framework/unmanaged-api/fusion/iassemblycache-interface.md)グローバル アセンブリ キャッシュを表すインスタンス。  
  
 [CreateAssemblyEnum 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblyenum-function.md)  
 ポインターを取得、 [IAssemblyEnum](../../../../docs/framework/unmanaged-api/fusion/iassemblyenum-interface.md)指定したアセンブリ内に存在するオブジェクトの一覧を表すインスタンス。  
  
 [CreateAssemblyNameObject 関数](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)  
 ポインターを取得、 [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)指定した名前のアセンブリの一意の id を表すインスタンス。  
  
 [CreateHistoryReader 関数](../../../../docs/framework/unmanaged-api/fusion/createhistoryreader-function.md)  
 指定したファイルの履歴のリーダーを作成します。  
  
 [CreateInstallReferenceEnum 関数](../../../../docs/framework/unmanaged-api/fusion/createinstallreferenceenum-function.md)  
 ポインターを取得、 [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)指定したアセンブリへのアプリケーションの参照のリストを表すインスタンス。  
  
 [GetAppIdAuthority 関数](../../../../docs/framework/unmanaged-api/fusion/getappidauthority-function.md)  
 ポインターを取得、 [IAppIdAuthority](../../../../docs/framework/unmanaged-api/fusion/iappidauthority-interface.md)アプリケーション id と参照のキーを管理するインスタンス。  
  
 [GetAssemblyIdentityFromFile 関数](../../../../docs/framework/unmanaged-api/fusion/getassemblyidentityfromfile-function.md)  
 ポインターを取得、 `IUnknown` 、指定したオブジェクト`IID`のアセンブリにある指定したファイル パス。  
  
 [GetCachePath 関数](../../../../docs/framework/unmanaged-api/fusion/getcachepath-function.md)  
 指定したフラグを使用して、キャッシュされたアセンブリへのパスを取得します。  
  
 [GetHistoryFileDirectory 関数](../../../../docs/framework/unmanaged-api/fusion/gethistoryfiledirectory-function.md)  
 アプリケーション履歴ディレクトリのパスを取得します。  
  
 [GetIdentityAuthority 関数](../../../../docs/framework/unmanaged-api/fusion/getidentityauthority-function.md)  
 ポインターを取得、 [IIdentityAuthority](../../../../docs/framework/unmanaged-api/fusion/iidentityauthority-interface.md)コード オブジェクトのキーを管理するインスタンス。  
  
 [IsFrameworkAssembly 関数](../../../../docs/framework/unmanaged-api/fusion/isframeworkassembly-function.md)  
 指定したアセンブリが管理されているかどうかを示す値を取得します。  
  
 [NukeDownloadedCache 関数](../../../../docs/framework/unmanaged-api/fusion/nukedownloadedcache-function.md)  
 共通言語ランタイムのダウンロード キャッシュを削除します。  
  
 [PreBindAssemblyEx 関数](../../../../docs/framework/unmanaged-api/fusion/prebindassemblyex-function.md)  
 アセンブリのポリシー適用後の表示名を取得します。  
  
## <a name="related-sections"></a>関連項目  
 [Fusion インターフェイス](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
  
 [Fusion 列挙型](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)  
  
 [Fusion 構造体](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)  
  
 [グローバル アセンブリ キャッシュ](../../../../docs/framework/app-domains/gac.md)
