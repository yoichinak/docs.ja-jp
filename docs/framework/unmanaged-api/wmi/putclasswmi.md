---
title: PutClassWmi 関数 (アンマネージ API リファレンス)
description: PutClassWmi 関数では、新しいクラスを作成します。 または、既存のものを更新します。
ms.date: 11/06/2017
api_name:
- PutClassWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutClassWmi
helpviewer_keywords:
- PutClassWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f9d537f7713233d363f7d408b1cef0485d99d981
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365699"
---
# <a name="putclasswmi-function"></a>PutClassWmi 関数

新しいクラスが作成されるか、既存のクラスが更新されます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT PutClassWmi (
   [in] IWbemClassObject*    pObject,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>パラメーター

`pObject`\
[in]有効なクラス定義へのポインター。 すべての必要なプロパティ値が正しく初期化する必要があります。

`lFlags`\
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | 場合設定、WMI では、修正済みのフレーバーで、修飾子は保存されません。 <br> 指定しない場合、このオブジェクトがローカライズされていないことと、すべての修飾子がこのインスタンスに格納されていること前提は、セット。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 存在したり、既に存在する場合は、上書きしない場合は、クラスを作成します。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | クラスを更新します。 クラスは、呼び出しの成功に存在する必要があります。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | クラスを作成します。 クラスが既に存在する場合、呼び出しが失敗します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグには、半同期的メソッドの呼び出しが行わします。 |
| `WBEM_FLAG_OWNER_UPDATE` | 0x10000 | 呼び出すときに、プッシュのプロバイダーはこのフラグを指定する必要があります`PutClassWmi`をこのクラスが変更されたことを示します。 |
| `WBEM_FLAG_UPDATE_COMPATIBLE` | 0 | クラスが派生クラスを持たないとそのクラスのインスタンスがない場合に更新するできるようにします。 説明の修飾子などの重要でない修飾子だけを変更した場合、更新プログラムは、すべてのケースでことも可能に。 クラスのインスタンスには、または変更が重要な修飾子には、更新プログラムは失敗します。 |
| `WBEM_FLAG_UPDATE_SAFE_MODE` | 0x20 | 変更に子クラスを任意の競合が発生しない限り、子クラスがある場合でもクラスの更新が可能です。 たとえば、このフラグは、子クラスのいずれかで記述されていない基底クラスに追加する新しいプロパティを使用できます。 クラスのインスタンスの場合、更新は失敗します。 |
| `WBEM_FLAG_UPDATE_FORCE_MODE` | 0x40 | 競合する子クラスが存在する場合は、クラスの更新プログラムを強制的にします。 たとえば、このフラグは、更新プログラム クラス修飾子は、子クラスで定義されていて、基底クラスが、同じ修飾子を追加しようとしています。 既存のものと競合します。 強制モードでは、子クラスに競合する修飾子を削除することによって tis 競合を解決します。 |

`pCtx`\
[in]この値は、通常、`null`します。 ポインターは、それ以外の場合、 [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)インスタンスを要求されたクラスを提供しているプロバイダーによって使用されることができます。

`ppCallResult`\
[out]場合`null`、このパラメーターは使用されません。 場合`lFlags`を含む`WBEM_FLAG_RETURN_IMMEDIATELY`、関数を直ちに返します`WBEM_S_NO_ERROR`します。 `ppCallResult`パラメーターは、新しいへのポインターを受け取ります[IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult)オブジェクト。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、作成またはクラスを変更するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | 指定したクラスが無効です。 通常、これが示す`pObject`インスタンス オブジェクトを指定します。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_INVALID OPERATION` | 0x80041016 | 指定されたクラス名が無効です。 |
| `WBEM_E_CLASS_HAS_CHILDREN` | 0x80041025 | サブクラスを無効にする変更が試行されました。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、クラスが既に存在します。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` 指定された`lFlags`クラスが見つかりません。 |
| `WBEM_E_INCOMPLETE_CLASS` | 0x80041020 | クラスの必須プロパティがすべてではなく設定されています。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI のリモート プロシージャ コール (RPC) リンクに失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。  |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemServices::PutClass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putclass)メソッド。

ユーザーは、アンダー スコア文字で開始または終了する名前を持つクラスを作成しない可能性があります。

呼び出すことによって追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)