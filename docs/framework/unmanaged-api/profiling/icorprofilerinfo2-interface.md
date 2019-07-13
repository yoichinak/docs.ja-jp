---
title: ICorProfilerInfo2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2
helpviewer_keywords:
- ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: 91bd49b6-4d12-494f-a8f1-2f251e8c65e3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3476a338191a4af9cc01b7e44456f1bd20f52a10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796547"
---
# <a name="icorprofilerinfo2-interface"></a>ICorProfilerInfo2 インターフェイス
コード プロファイラーが共通言語ランタイム (CLR) イベントの監視を制御する、要求の情報との通信に使用するメソッドを提供します。 `ICorProfilerInfo2`インターフェイスの拡張機能は、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)インターフェイス。 つまり、.NET Framework version 2.0 およびそれ以降のバージョンでサポートされている新しいメソッドが用意されています。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[DoStackSnapshot メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)|マネージ呼び出しフレームをプロファイラーに報告する、指定されたスレッドのスタックについて説明します。|  
|[EnumModuleFrozenObjects メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)|指定したモジュールに固定されたオブジェクトに対して反復処理する列挙子を取得します。|  
|[GetAppDomainStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getappdomainstaticaddress-method.md)|指定したアプリケーション ドメインのスコープ内の指定されたアプリケーション ドメインの静的フィールドのアドレスを取得します。|  
|[GetArrayObjectInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getarrayobjectinfo-method.md)|配列オブジェクトに関する詳細な情報を取得します。|  
|[GetBoxClassLayout メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getboxclasslayout-method.md)|ボックス化は、指定した値型のクラス レイアウトに関する情報を取得します。|  
|[GetClassFromTokenAndTypeArgs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)|取得、`ClassID`指定したメタデータ トークンを使用して型の`ClassID`いずれかの値が引数を入力します。|  
|[GetClassIDInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)|指定のジェネリック クラス、クラスのメタデータ トークンの親モジュールを取得、`ClassID`その親クラスの`ClassID`クラスの存在する場合、各型引数。|  
|[GetClassLayout メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclasslayout-method.md)|指定したクラスで定義されるフィールドのメモリ内レイアウトに関する情報を取得します。 つまり、このメソッドはクラスのフィールドのオフセットを取得します。|  
|[GetCodeInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)|指定した `FunctionID` に関連付けられているネイティブ コードの範囲を取得します。|  
|[GetContextStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcontextstaticaddress-method.md)|指定したコンテキストのスコープ内の指定したコンテキストの静的フィールドのアドレスを取得します。|  
|[GetFunctionFromTokenAndTypeArgs メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)|取得、`FunctionID`クラスを格納している、指定したメタデータ トークンを使用して関数のおよび`ClassID`のいずれかの値が引数を入力します。|  
|[GetFunctionInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)|関数の親クラス、メタデータ トークン、および型引数が存在する場合はそれぞれの `ClassID` を取得します。|  
|[GetGenerationBounds メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)|ガベージ コレクション ヒープのジェネレーションを構成するメモリ領域 (ヒープのセグメント) を取得します。|  
|[GetNotifiedExceptionClauseInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getnotifiedexceptionclauseinfo-method.md)|例外の句のネイティブのアドレスとフレームの情報を取得します (`catch`/`finally`/`filter`) を実行するのには、またはが実行されています。|  
|[GetObjectGeneration メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)|指定したオブジェクトが含まれるヒープのセグメントを取得します。|  
|[GetRVAStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getrvastaticaddress-method.md)|指定された相対仮想アドレス (RVA) のアドレスを取得します。-静的フィールド。|  
|[GetStaticFieldInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstaticfieldinfo-method.md)|指定したフィールドの静的なスコープを取得します。|  
|[GetStringLayout メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md)|文字列オブジェクトのレイアウトに関する情報を取得します。|  
|[GetThreadAppDomain メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)|指定したスレッドが実行されているコードのアプリケーション ドメインの ID を取得します。|  
|[GetThreadStaticAddress メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md)|指定したスレッドのスコープ内の指定したスレッド内静的フィールドのアドレスを取得します。|  
|[SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)|「入力」、「のまま」、およびマネージ関数の"tailcall"フックで呼び出されるプロファイラー実装関数を指定します。|  
  
## <a name="remarks"></a>Remarks  
 プロファイラーでメソッドを呼び出し、`ICorProfilerInfo2`イベントの監視を制御し、情報を要求するには、CLR と通信するインターフェイス。  
  
 メソッド、`ICorProfilerInfo2`インターフェイスは、フリー スレッド モデルを使用して、CLR によって実装されます。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
 CLR から渡される、`ICorProfilerInfo2`へのプロファイラーの実装を使用して初期化中に、各コード プロファイラーのインターフェイス[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)します。 コード プロファイラーは、のメソッドを呼び出すことができますし、 `ICorProfilerInfo2` CLR の制御下で実行されているマネージ コードに関する情報を取得するインターフェイス。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
