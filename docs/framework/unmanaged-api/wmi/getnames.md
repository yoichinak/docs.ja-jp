---
title: GetNames 関数 (アンマネージ API リファレンス)
description: GetNames 関数は、オブジェクトのプロパティの名前を取得します。
ms.date: 11/06/2017
api_name:
- GetNames
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- GetNames
helpviewer_keywords:
- GetNames function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e75bf9aab820216373f2f33fe8aa567f10befcb1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746524"
---
# <a name="getnames-function"></a>GetNames 関数
オブジェクトのプロパティの名前の一部またはすべてが取得されます。 

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
    
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetNames (
   [in] int                 vFunc, 
   [in] IWbemClassObject*   ptr, 
   [in] LPCWSTR             wszQualifierName,
   [in] LONG                lFlags,
   [in] VARIANT*            pQualifierValue,
   [out] SAFEARRAY (BSTR)** pstrNames
); 
```  

## <a name="parameters"></a>パラメーター

`vFunc`  
[in]このパラメーターは使用されません。

`ptr`  
[in]ポインター、 [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject)インスタンス。

`wszQualifierName`  
[in]有効なへのポインター`LPCWSTR`フィルターの一部として動作する修飾子の名前を指定します。 詳細については、次を参照してください。、[解説](#remarks)セクション。 このパラメーターは、`null` に設定できます。 

`lFlags`  
[in]ビット フィールドの組み合わせ。 詳細については、次を参照してください。、[解説](#remarks)セクション。

`pQualifierValue`   
[in]有効なへのポインター`VARIANT`フィルター値に初期化された構造体。 このパラメーターは、`null` に設定できます。 

`pstrNames`  
[out]A`SAFEARRAY`プロパティ名を含む構造体。 項目で、このパラメーターがありますへのポインター`null`します。 参照してください、[解説](#remarks)詳細についてはします。 

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
|`WBEM_E_FAILED` | 0x80041001 | 一般的なエラーが発生しました。 |
|`WBEM_E_INVALID_PARAMETER` | 0x80041008 | 1 つまたは複数のパラメーターが無効、またはフラグとパラメーターの組み合わせが正しくないが指定されました。 |
|`WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
|`WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |
  
## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemClassObject::GetNames](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-getnames)メソッド。

返される名前付きのフラグとパラメーターの組み合わせによって制御されます。 たとえば、関数では、すべてのプロパティの名前またはキーのプロパティの名前のみを返すことができます。  プライマリ フィルターがで指定された、`lFlags`パラメーター、およびその他のパラメーターは、これによって異なります。

フラグの値で`lFlags`ビット フィールドには

フラグとして渡すことができる、`lEnumFlags`引数はビット フィールドで定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。  その他のグループからのすべてのフラグでは、各グループから 1 つのフラグを組み合わせることができます。 ただし、同じグループからのフラグは、相互に排他的です。 

| フラグのグループ 1 |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_ALWAYS` | 0 | すべてのプロパティ名が返されます。 `strQualifierName` `pQualifierVal`使用されていません。 |
| `WBEM_FLAG_ONLY_IF_TRUE` | 1 | 指定した名前の修飾子を持つプロパティのみを返す、`strQualifierName`パラメーター。 かどうかは、このフラグが使用される、指定する必要あります`strQualifierName`します。 |
|`WBEM_FLAG_ONLY_IF_FALSE` | 2 |  指定された名前の修飾子がない唯一のプロパティを返す、`strQualifierName`パラメーター。 かどうかは、このフラグが使用される、指定する必要あります`strQualifierName`します。 |
|`WBEM_FLAG_ONLY_IF_IDENTICAL` | 3 | 指定した名前の修飾子を持つプロパティのみを返す、`wszQualifierName`パラメーターで指定されているのと同じ値が設定されても、`pQualifierVal`構造体。 このフラグを使用する場合、両方を指定する必要があります、`wszQualifierName`と`pQualifierValue`します。 |

| フラグのグループ 2 |値  |説明  |
|---------|---------|---------|
|`WBEM_FLAG_KEYS_ONLY` | 0x4 | キーを定義するプロパティの名前のみを返します。 |
|`WBEM_FLAG_REFS_ONLY` | 0x8 | 戻り値プロパティ名のみのオブジェクト参照であります。 |

| フラグのグループ 3 |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_LOCAL_ONLY` | 0x10 | 最派生クラスに属しているプロパティ名のみが返されます。 親クラスからプロパティを除外します。 |
| `WBEM_FLAG_PROPAGATED_ONLY` |  0x20 | 親クラスに属しているプロパティ名のみが返されます。 |
|`WBEM_FLAG_SYSTEM_ONLY` | 0x30 | システムのプロパティ名のみが返されます。 |
|`WBEM_FLAG_NONSYSTEM_ONLY` | 0x40 | 非システムのプロパティ名のみが返されます。 |

関数は常に新しい割り当て`SAFEARRAY`返された場合`WBEM_S_NO_ERROR`、および`pstrNames`は常に設定されます。 指定したフィルターに一致するプロパティがない場合、返される配列要素の 0 ことができます。 関数を以外の値を返す場合`WBM_S_NO_ERROR`、新しい`SAFEARRAY`構造は返されません。
 
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** WMINet_Utils.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)
