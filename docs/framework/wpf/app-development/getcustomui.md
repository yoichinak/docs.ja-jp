---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: 30084143949d2243fd310448c52e6b861505ad66
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191251"
---
# <a name="getcustomui"></a>GetCustomUI
実装されている場合に、カスタムの進行状況とエラー メッセージをホストから取得する PresentationHost.exe によって呼び出されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzProgressAssemblyName`  
  
 [out]ホストが指定した進行中のユーザー インターフェイスが含まれるアセンブリへのポインター。  
  
 `pwzProgressClassName`  
  
 [out]可能であれば、進行中のホストが指定したユーザー インターフェイスであるクラスの名前、[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]ファイルと<xref:System.Windows.Controls.Page>はその最上位要素です。 このクラスがで指定されているアセンブリに存在する`pwzProgressAssemblyName`します。  
  
 `pwzErrorAssemblyName`  
  
 [out]ホストが指定したエラーのユーザー インターフェイスが含まれるアセンブリへのポインター。  
  
 `pwzErrorClassName`  
  
 [out]ホストが指定したエラーのユーザーであるクラスの名前インターフェイス、可能であれば、XAML ファイルで<xref:System.Windows.Controls.Page>はその最上位要素です。 このクラスがで指定されているアセンブリに存在する`pwzErrorAssemblyName`します。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT:無視されます。  
  
## <a name="remarks"></a>Remarks  
 ホスト アプリケーションは、PresentationHost.exe の既定のユーザー インターフェイスに準拠していない特定のテーマがあります。 大文字と小文字の場合は、ホスト アプリケーションを実装できます[GetCustomUI](getcustomui.md)進行状況とエラー ユーザー インターフェイスを PresentationHost.exe に戻ります。 PresentationHost.exe は常に呼び出さ[GetCustomUI](getcustomui.md)の既定のユーザー インターフェイスを使用する前にします。  
  
 この関数は、PresentationHost の初期化中に 1 回呼び出されます。  
  
## <a name="see-also"></a>関連項目

- [IWpfHostSupport](iwpfhostsupport.md)
