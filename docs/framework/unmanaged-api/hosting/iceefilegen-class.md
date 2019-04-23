---
title: ICeeFileGen クラス
ms.date: 03/30/2017
api_name:
- ICeeFileGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeFileGen
helpviewer_keywords:
- ICeeFileGen class [.NET Framework hosting]
ms.assetid: 90368606-506e-40df-be1f-8d595159203f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb0e7a676fdbbe3cf04108266471833b28275b1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083571"
---
# <a name="iceefilegen-class"></a>ICeeFileGen クラス
ネイティブ ポータブル実行可能 (PE) ファイルを作成するための機能を提供します。 インターフェイスは、実行可能ファイルのコンパイル済み出力を生成するコンパイラで通常使用されます。  
  
> [!NOTE]
>  `ICeeFileGen` .NET Framework インフラストラクチャをサポートし、コードから直接使用するものではありません。  
  
 このインターフェイスは非推奨とされましたを将来のリリースで削除されます。  
  
## <a name="syntax"></a>構文  
  
```  
class ICeeFileGen {  
public:  
    virtual HRESULT CreateCeeFile(HCEEFILE *ceeFile);  
  
    virtual HRESULT EmitMetaData (HCEEFILE ceeFile,  
        IMetaDataEmit *emitter, mdScope scope);  
  
    virtual HRESULT EmitLibraryName (HCEEFILE ceeFile,  
        IMetaDataEmit *emitter, mdScope scope);  
  
    virtual HRESULT EmitMethod ();  
  
    virtual HRESULT GetMethodRVA (HCEEFILE ceeFile,  
        ULONG codeOffset, ULONG *codeRVA);  
  
    virtual HRESULT EmitSignature ();  
  
    virtual HRESULT EmitString (HCEEFILE ceeFile,  
        __in LPWSTR strValue, ULONG *strRef);  
  
    virtual HRESULT GenerateCeeFile (HCEEFILE ceeFile);  
  
    virtual HRESULT SetOutputFileName (HCEEFILE ceeFile,  
        __in LPWSTR outputFileName);  
  
    virtual HRESULT GetOutputFileName (HCEEFILE ceeFile,  
        __out LPWSTR *outputFileName);  
  
    virtual HRESULT SetResourceFileName (HCEEFILE ceeFile,  
        __in LPWSTR resourceFileName);  
  
    virtual HRESULT GetResourceFileName (HCEEFILE ceeFile,  
        __out LPWSTR *resourceFileName);  
  
    virtual HRESULT SetImageBase(HCEEFILE ceeFile, size_t imageBase);  
  
    virtual HRESULT SetSubsystem(HCEEFILE ceeFile, DWORD subsystem,  
        DWORD major, DWORD minor);  
  
    virtual HRESULT SetEntryClassToken ();  
  
    virtual HRESULT GetEntryClassToken ();  
  
    virtual HRESULT SetEntryPointDescr ();  
  
    virtual HRESULT GetEntryPointDescr ();  
  
    virtual HRESULT SetEntryPointFlags ();  
  
    virtual HRESULT GetEntryPointFlags ();  
  
    virtual HRESULT SetDllSwitch (HCEEFILE ceeFile, BOOL dllSwitch);  
  
    virtual HRESULT GetDllSwitch (HCEEFILE ceeFile, BOOL *dllSwitch);  
  
    virtual HRESULT SetLibraryName (HCEEFILE ceeFile,  
        __in LPWSTR LibraryName);  
  
    virtual HRESULT GetLibraryName (HCEEFILE ceeFile,  
        __out LPWSTR *LibraryName);  
  
    virtual HRESULT SetLibraryGuid (HCEEFILE ceeFile,  
        __in LPWSTR LibraryGuid);  
  
    virtual HRESULT DestroyCeeFile(HCEEFILE *ceeFile);  
  
    virtual HRESULT GetSectionCreate (HCEEFILE ceeFile,  
        const char *name, DWORD flags, HCEESECTION *section);  
  
    virtual HRESULT GetIlSection (HCEEFILE ceeFile,  
        HCEESECTION *section);  
  
    virtual HRESULT GetRdataSection (HCEEFILE ceeFile,  
        HCEESECTION *section);  
  
    virtual HRESULT GetSectionDataLen (HCEESECTION section,  
        ULONG *dataLen);  
  
    virtual HRESULT GetSectionBlock (HCEESECTION section, ULONG len,  
        ULONG align=1, void **ppBytes=0);  
  
    virtual HRESULT TruncateSection (HCEESECTION section, ULONG len);  
  
    virtual HRESULT AddSectionReloc (HCEESECTION section,  
        ULONG offset, HCEESECTION relativeTo,  
        CeeSectionRelocType relocType);  
  
    virtual HRESULT SetSectionDirectoryEntry (HCEESECTION section,  
        ULONG num);  
  
    virtual HRESULT CreateSig ();  
  
    virtual HRESULT AddSigArg ();  
  
    virtual HRESULT SetSigReturnType ();  
  
    virtual HRESULT SetSigCallingConvention ();  
  
    virtual HRESULT DeleteSig ();  
  
    virtual HRESULT SetEntryPoint (HCEEFILE ceeFile,  
        mdMethodDef method);  
  
    virtual HRESULT GetEntryPoint (HCEEFILE ceeFile,  
        mdMethodDef *method);  
  
    virtual HRESULT SetComImageFlags (HCEEFILE ceeFile, DWORD mask);  
  
    virtual HRESULT GetComImageFlags (HCEEFILE ceeFile, DWORD *mask);  
  
    virtual HRESULT GetIMapTokenIface(HCEEFILE ceeFile,  
        IMetaDataEmit *emitter, IUnknown **pIMapToken);  
  
    virtual HRESULT SetDirectoryEntry (HCEEFILE ceeFile,  
        HCEESECTION section, ULONG num, ULONG size, ULONG offset = 0);  
  
    virtual HRESULT EmitMetaDataEx (HCEEFILE ceeFile,  
        IMetaDataEmit *emitter);   
  
    virtual HRESULT EmitLibraryNameEx (HCEEFILE ceeFile,  
        IMetaDataEmit *emitter);  
  
    virtual HRESULT GetIMapTokenIfaceEx(HCEEFILE ceeFile,  
        IMetaDataEmit *emitter, IUnknown **pIMapToken);  
  
    virtual HRESULT EmitMacroDefinitions(HCEEFILE ceeFile,  
        void *pData, DWORD cData);  
  
    virtual HRESULT CreateCeeFileFromICeeGen(ICeeGen *pFromICeeGen,  
        HCEEFILE *ceeFile, DWORD createFlags =  
        ICEE_CREATE_FILE_PURE_IL);  
  
    virtual HRESULT SetManifestEntry(HCEEFILE ceeFile, ULONG size,  
        ULONG offset);  
  
    virtual HRESULT SetEnCRVABase(HCEEFILE ceeFile, ULONG dataBase,  
        ULONG rdataBase);  
  
    virtual HRESULT GenerateCeeMemoryImage (HCEEFILE ceeFile,  
        void **ppImage);  
  
    virtual HRESULT ComputeSectionOffset(HCEESECTION section,  
        __in char *ptr, unsigned *offset);  
  
    virtual HRESULT ComputeOffset(HCEEFILE file, __in char *ptr,  
        HCEESECTION *pSection, unsigned *offset);  
  
    virtual HRESULT GetCorHeader(HCEEFILE ceeFile,  
        IMAGE_COR20_HEADER **header);  
  
    virtual HRESULT LinkCeeFile (HCEEFILE ceeFile);  
  
    virtual HRESULT FixupCeeFile (HCEEFILE ceeFile);  
  
    virtual HRESULT GetSectionRVA (HCEESECTION section, ULONG *rva);  
  
    virtual HRESULT ComputeSectionPointer(HCEESECTION section,  
        ULONG offset, __out char **ptr);  
  
    virtual HRESULT SetObjSwitch (HCEEFILE ceeFile, BOOL objSwitch);  
  
    virtual HRESULT GetObjSwitch (HCEEFILE ceeFile, BOOL *objSwitch);  
  
    virtual HRESULT SetVTableEntry(HCEEFILE ceeFile, ULONG size,  
        ULONG offset);  
  
    virtual HRESULT SetStrongNameEntry(HCEEFILE ceeFile, ULONG size,  
        ULONG offset);  
  
    virtual HRESULT EmitMetaDataAt (HCEEFILE ceeFile,  
        IMetaDataEmit *emitter, HCEESECTION section, DWORD offset,  
        BYTE* buffer, unsigned buffLen);  
  
    virtual HRESULT GetFileTimeStamp (HCEEFILE ceeFile,  
        DWORD *pTimeStamp);  
  
    virtual HRESULT AddNotificationHandler(HCEEFILE ceeFile,  
        IUnknown *pHandler);  
  
    virtual HRESULT SetFileAlignment(HCEEFILE ceeFile,  
        ULONG fileAlignment);  
  
    virtual HRESULT ClearComImageFlags (HCEEFILE ceeFile, DWORD mask);  
  
    virtual HRESULT CreateCeeFileEx(HCEEFILE *ceeFile,  
        ULONG createFlags);  
  
    virtual HRESULT SetImageBase64(HCEEFILE ceeFile,  
        ULONGLONG imageBase);  
  
    virtual HRESULT GetHeaderInfo (HCEEFILE ceeFile,  
        PIMAGE_NT_HEADERS *ppNtHeaders,  
        PIMAGE_SECTION_HEADER *ppSections, ULONG *pNumSections);  
  
    virtual HRESULT CreateCeeFileEx2(HCEEFILE *ceeFile,  
        ULONG createFlags, LPCWSTR seedFileName = NULL);  
  
    virtual HRESULT SetVTableEntry64(HCEEFILE ceeFile, ULONG size,  
        void* ptr);  
};  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** ICeeFileGen.h  
  
 **.NET framework のバージョン:** 1  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
