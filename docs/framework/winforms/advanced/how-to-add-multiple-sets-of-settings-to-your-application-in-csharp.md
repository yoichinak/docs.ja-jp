---
title: '方法: C# のアプリケーションに複数の設定セットを追加する'
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], multiple sets
- application settings [Windows Forms], C#
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
ms.openlocfilehash: 106e0ee0b8775f329f3ffd8babe458cac8492bd5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187383"
---
# <a name="how-to-add-multiple-sets-of-settings-to-your-application-in-c"></a>方法: C 言語でアプリケーションに複数の設定セットを追加します。\#
場合によっては、アプリケーションで複数の設定のセットがある可能性があります。 たとえば、アプリケーションを開発し、頻繁に変更する設定の特定のグループが必要な場合は場合があります、ファイルごとに、置換できるように、すべて 1 つのファイルにそれらを分離するその他の設定の影響を受けていません。 Visual Studio プロジェクトに複数の設定セットを追加することができます。 設定の追加セットは、Properties.Settings オブジェクトを使用してアクセスできます。  
  
### <a name="to-add-an-additional-set-of-setting-to-your-application"></a>アプリケーションに追加の設定セットを追加するには  
  
1.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **[新しい項目の追加]** ダイアログ ボックスが開きます。  
  
2.  **新しい項目の追加**ダイアログ ボックスで、**設定ファイル**ファイルの名前を入力し、をクリックして、**追加**をソリューションに新しい設定ファイルを追加します。  
  
3.  **ソリューション エクスプ ローラー**に、新しい設定ファイルをドラッグして、**プロパティ**フォルダー。 これにより、コードで使用できる新しい設定ができます。  
  
4.  追加し、他の設定ファイルと同様に、このファイルの設定を使用します。 この Properties.Settings オブジェクトを使用して設定のグループにアクセスできます。  
  
## <a name="see-also"></a>関連項目

- [アプリケーション設定とユーザー設定の使用](using-application-settings-and-user-settings.md)
- [アプリケーション設定の概要](application-settings-overview.md)
