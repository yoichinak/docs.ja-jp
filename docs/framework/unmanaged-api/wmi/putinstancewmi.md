---
title: PutInstanceWmi 関数 (アンマネージ API リファレンス)
description: PutInstanceWmi 関数を作成または既存のクラスのインスタンスを更新します。
ms.date: 11/06/2017
api_name:
- PutInstanceWmi
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- PutInstanceWmi
helpviewer_keywords:
- PutInstanceWmi function [.NET WMI and performance counters]
topic_type:
- Reference
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 19f657fd76f73c4016824511079e6f037bc3bc53
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359377"
---
# <a name="putinstancewmi-function"></a>PutInstanceWmi 関数

既存のクラスのインスタンスが作成または更新されます。 インスタンスは、WMI リポジトリに書き込まれます。

[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT PutInstanceWmi (
   [in] IWbemClassObject*    pInst,
   [in] long                 lFlags,
   [in] IWbemContext*        pCtx,
   [out] IWbemCallResult**   ppCallResult
);
```

## <a name="parameters"></a>パラメーター

`pInst`\
[in]書き込まれるインスタンスへのポインター。

`lFlags`\
[in]この関数の動作に影響するフラグの組み合わせ。 次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_FLAG_USE_AMENDED_QUALIFIERS` | 0x20000 | かどうか設定、WMI は保存されませんで任意の修飾子、 **Amended**フレーバー。 <br> 指定しない場合、このオブジェクトがローカライズされていないことと、すべての修飾子がこのインスタンスに格納されていること前提は、セット。 |
| `WBEM_FLAG_CREATE_OR_UPDATE` | 0 | 存在したり、既に存在する場合は、上書きしない場合は、インスタンスを作成します。 |
| `WBEM_FLAG_UPDATE_ONLY` | 1 | インスタンスを更新します。 呼び出しが成功するは、インスタンスが存在する必要があります。 |
| `WBEM_FLAG_CREATE_ONLY` | 2 | インスタンスを作成します。 インスタンスが既に存在する場合、呼び出しが失敗します。 |
| `WBEM_FLAG_RETURN_IMMEDIATELY` | 0x10 | フラグには、半同期的メソッドの呼び出しが行わします。 |

`pCtx`\
[in]この値は、通常、`null`します。 ポインターは、それ以外の場合、 [IWbemContext](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcontext)インスタンスを要求されたクラスを提供しているプロバイダーによって使用されることができます。

`ppCallResult`\
[out]場合`null`、このパラメーターは使用されません。 場合`lFlags`を含む`WBEM_FLAG_RETURN_IMMEDIATELY`、関数を直ちに返します`WBEM_S_NO_ERROR`します。 `ppCallResult`パラメーターは、新しいへのポインターを受け取ります[IWbemCallResult](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemcallresult)オブジェクト。

## <a name="return-value"></a>戻り値

この関数によって返される次の値が定義されている、 *WbemCli.h*ヘッダー ファイル、またはすることができますに定数としてコードで定義します。

|定数  |値  |説明  |
|---------|---------|---------|
| `WBEM_E_ACCESS_DENIED` | 0x80041003 | ユーザーには、指定したクラスのインスタンスを更新するアクセス許可がありません。 |
| `WBEM_E_FAILED` | 0x80041001 | 不明なエラーが発生しました。 |
| `WBEM_E_INVALID_CLASS` | 0x80041010 | このインスタンスをサポートしているクラスが無効です。 |
| `WBEM_E_ILLEGAL_NULL` | 0x80041028 | `null`できないプロパティが指定されました`null`、いずれかでマークされているなど、**インデックス**または**not_** 修飾子。 |
| `WBEM_E_INVALID_OBJECT` | 0x8004100f | 指定したインスタンスが無効です。 (たとえば、呼び出し`PutInstanceWmi`クラスには、この値を返します)。 |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | パラメーターが無効です。 |
| `WBEM_E_ALREADY_EXISTS` | 0x80041019 | `WBEM_FLAG_CREATE_ONLY`フラグが指定されましたが、インスタンスが既に存在します。 |
| `WBEM_E_NOT_FOUND` | 0x80041002 | `WBEM_FLAG_UPDATE_ONLY` 指定された`lFlags`が、インスタンスが存在しません。 |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | 操作を完了するのに十分なメモリがあります。 |
| `WBEM_E_SHUTTING_DOWN` | 0x80041033 | WMI は、おそらく停止および再起動されました。 呼び出す[ConnectServerWmi](connectserverwmi.md)もう一度です。 |
| `WBEM_E_TRANSPORT_FAILURE` | 0x80041015 | 現在のプロセスと WMI のリモート プロシージャ コール (RPC) リンクに失敗しました。 |
| `WBEM_S_NO_ERROR` | 0 | 関数呼び出しに成功しました。 |

## <a name="remarks"></a>Remarks

この関数の呼び出しをラップする、 [IWbemServices::PutInstance](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemservices-putinstance)メソッド。

`PutInstanceWmi`関数のインスタンスを作成して、既存クラスのインスタンスの更新をサポートします。  方法に応じて`pCtx`パラメーターが設定されていると、一部またはすべてのインスタンスのプロパティを更新します。

ときに、インスタンスによって示される`pInst`サブクラスが派生するクラスを担当するすべてのプロバイダーの呼び出し、サブクラスでは、Windows の管理に属しています。 元のこれらのプロバイダーのすべてが成功する必要があります`PutInstanceWmi`の要求に成功します。 階層の最上位のクラスをサポートしているプロバイダーが呼び出されます。 呼び出しの順序が最上位のクラスのサブクラスを続行し、Windows 管理によって示されるインスタンスを所有しているクラスのプロバイダーに到達するまで、上から下に進みます`pInst`します。
Windows の管理には、インスタンスの子クラスのいずれかのプロバイダーは呼び出されません。

アプリケーションが、クラス階層に属しているインスタンスを更新する必要がありますと、`pInst`パラメーターは、変更するプロパティを含むインスタンスを指す必要があります。 つまり、ターゲット インスタンスが属しているを検討**ClassB**します。 **ClassB**から派生したインスタンス**ClassA**、および**ClassA**プロパティを定義**PropA**します。 アプリケーションがの値を変更するか**PropA**で、 **ClassB**設定する必要がありますのインスタンス、`pInst`のインスタンスではなく、そのインスタンスに**ClassA**.

呼び出す`PutInstanceWmi`抽象クラスのインスタンスでは許可されていません。

呼び出すことによって追加のエラー情報を取得するには、関数呼び出しに失敗した場合、 [GetErrorInfo](geterrorinfo.md)関数。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** WMINet_Utils.idl

**.NET Framework のバージョン:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>関連項目

- [WMI およびパフォーマンス カウンター (アンマネージ API リファレンス)](index.md)