---
ms.openlocfilehash: e613f0c52c77efebf250f5935d5cbfc29bc09a6b
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760451"
---
### <a name="wpf-printing-stack-update"></a>WPF での印刷スタックの更新

|   |   |
|---|---|
|説明|<xref:System.Printing.PrintQueue?displayProperty=name> を使う WPF の印刷 API は、非推奨になった XPS 印刷 API ではなく Windows ドキュメント印刷パッケージ API を呼び出すようになりました。 この変更はサービス性を考慮して行われたもので、ユーザーも開発者も、動作または API の使用の変化を目にすることはありません。 Windows 10 Creators Update で実行すると、新しい印刷スタックは既定で有効になります。 以前のバージョンの Windows では、以前の印刷スタックが引き続き同じように動作します。|
|提案される解決策|Windows 10 Creators Update で以前のスタックを使用するには、<code>HKEY_CURRENT_USER\Software\Microsoft\.NETFramework\Windows Presentation Foundation\Printing</code> レジストリ キーの <code>UseXpsOMPrinting</code> REG_DWORD 値を <code>1</code> に設定します。|
|スコープ|エッジ|
|Version|4.7|
|型|ランタイム|

