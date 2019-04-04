---
title: 文字列に対する既定のマーシャリング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings, interop marshaling
- interop marshaling, strings
ms.assetid: 9baea3ce-27b3-4b4f-af98-9ad0f9467e6f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aeba97a5caef8fc705a3b04496ce1fd17085ec5d
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409316"
---
# <a name="default-marshaling-for-strings"></a>文字列に対する既定のマーシャリング
<xref:System.String?displayProperty=nameWithType> と <xref:System.Text.StringBuilder?displayProperty=nameWithType> クラスのマーシャリング動作は類似しています。  
  
 文字列は、COM スタイル `BSTR` 型または null で終わる文字列 (null 文字で終わる文字配列) としてマーシャリングされます。 文字列内の文字は、Unicode (Windows システムでの既定値) または ANSI としてマーシャリングすることができます。  
  
 このトピックでは、文字列型のマーシャリングに関する以下の情報を示します。  
  
-   [インターフェイスで使用される文字列](#cpcondefaultmarshalingforstringsanchor1)  
  
-   [プラットフォーム呼び出しで使用される文字列](#cpcondefaultmarshalingforstringsanchor5)  
  
-   [構造体で使用される文字列](#cpcondefaultmarshalingforstringsanchor2)  
  
-   [固定長文字列バッファー](#cpcondefaultmarshalingforstringsanchor3)  
  
<a name="cpcondefaultmarshalingforstringsanchor1"></a>

## <a name="strings-used-in-interfaces"></a>インターフェイスで使用される文字列  
 次の表は、アンマネージ コードへのメソッド引数としてマーシャリングするときの、文字列データ型のマーシャリングのオプションを示しています。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、COM インターフェイスへの文字列をマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。  
  
|列挙型|アンマネージ形式の説明|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr` (既定値)|長さと Unicode 文字がプレフィックスされた COM スタイル `BSTR`。|  
|`UnmanagedType.LPStr`|ANSI 文字の null で終わる配列へのポインター。|  
|`UnmanagedType.LPWStr`|Unicode 文字の null で終わる配列へのポインター。|  
  
 この表は文字列に適用されます。 ただし、<xref:System.Text.StringBuilder> の場合、許可される唯一のオプションは `UnmanagedType.LPStr` と `UnmanagedType.LPWStr`です。  
  
 以下の例では、`IStringWorker` インターフェイスで宣言された文字列を示します。  
  
```cpp  
public interface IStringWorker {  
void PassString1(String s);  
void PassString2([MarshalAs(UnmanagedType.BStr)]String s);  
void PassString3([MarshalAs(UnmanagedType.LPStr)]String s);  
void PassString4([MarshalAs(UnmanagedType.LPWStr)]String s);  
void PassStringRef1(ref String s);  
void PassStringRef2([MarshalAs(UnmanagedType.BStr)]ref String s);  
void PassStringRef3([MarshalAs(UnmanagedType.LPStr)]ref String s);  
void PassStringRef4([MarshalAs(UnmanagedType.LPWStr)]ref String s);  
);
```

以下の例では、タイプ ライブラリに記述された対応するインターフェイスを示します。

```
[…]  
interface IStringWorker : IDispatch {  
HRESULT PassString1([in] BSTR s);  
HRESULT PassString2([in] BSTR s);  
HRESULT PassString3([in] LPStr s);  
HRESULT PassString4([in] LPWStr s);  
HRESULT PassStringRef1([in, out] BSTR *s);  
HRESULT PassStringRef2([in, out] BSTR *s);  
HRESULT PassStringRef3([in, out] LPStr *s);  
HRESULT PassStringRef4([in, out] LPWStr *s);  
);
```

<a name="cpcondefaultmarshalingforstringsanchor5"></a>

## <a name="strings-used-in-platform-invoke"></a>プラットフォーム呼び出しで使用される文字列  
 プラットフォーム呼び出しは、文字列の引数を、.NET Framework 形式 (Unicode) から、プラットフォーム アンマネージ形式に変換してコピーします。 文字列は不変であり、呼び出しが戻るときに、アンマネージド メモリから元のマネージド メモリにコピーされることはありません。  
  
 次の表は、文字列をプラットフォーム呼び出しのメソッド引数としてマーシャリングする際のマーシャリング オプションをリストしています。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、文字列をマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。  
  
|列挙型|アンマネージ形式の説明|  
|----------------------|-------------------------------------|  
|`UnmanagedType.AnsiBStr`|長さと ANSI 文字がプレフィックスされた COM スタイル `BSTR`。|  
|`UnmanagedType.BStr`|長さと Unicode 文字がプレフィックスされた COM スタイル `BSTR`。|  
|`UnmanagedType.LPStr`|ANSI 文字の null で終わる配列へのポインター。|  
|`UnmanagedType.LPTStr`|プラットフォーム依存文字の null で終わる配列へのポインター。|  
|`UnmanagedType.LPWStr`|Unicode 文字の null で終わる配列へのポインター。|  
|`UnmanagedType.TBStr`|長さとプラットフォーム依存文字がプレフィックスされた COM スタイル `BSTR`。|  
|`VBByRefStr`|Visual Basic .NET で、アンマネージド コードの文字列を変更し、結果をマネージド コードに反映できるようにする値。 この値は、プラットフォーム呼び出しでだけサポートされます。 これが、`ByVal` 文字列の Visual Basic での既定値です。|  
  
 この表は文字列に適用されます。 ただし、<xref:System.Text.StringBuilder> の場合、許可される唯一のオプションは `LPStr`、`LPTStr`、および `LPWStr` です。  
  
 次の型定義は、プラットフォーム呼び出しで `MarshalAsAttribute` を使用するための正しい方法を示しています。  
  
```vb  
Class StringLibAPI      
Public Declare Auto Sub PassLPStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPStr)> s As String)      
Public Declare Auto Sub PassLPWStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPWStr)> s As String)      
Public Declare Auto Sub PassLPTStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.LPTStr)> s As String)      
Public Declare Auto Sub PassBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.BStr)> s As String)      
Public Declare Auto Sub PassAnsiBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.AnsiBStr)> s As String)      
Public Declare Auto Sub PassTBStr Lib "StringLib.Dll" _  
(<MarshalAs(UnmanagedType.TBStr)> s As String)  
End Class  
```

```csharp
class StringLibAPI {  
[DllImport("StringLib.Dll")]  
public static extern void PassLPStr([MarshalAs(UnmanagedType.LPStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPWStr([MarshalAs(UnmanagedType.LPWStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassLPTStr([MarshalAs(UnmanagedType.LPTStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassBStr([MarshalAs(UnmanagedType.BStr)]  
String s);  
[DllImport("StringLib.Dll")]  
public static extern void   
PassAnsiBStr([MarshalAs(UnmanagedType.AnsiBStr)]String s);  
[DllImport("StringLib.Dll")]  
public static extern void PassTBStr([MarshalAs(UnmanagedType.TBStr)]  
String s);  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor2"></a>   
## <a name="strings-used-in-structures"></a>構造体で使用される文字列  
 文字列は構造体の有効なメンバーです。ただし、<xref:System.Text.StringBuilder> バッファーは構造体では無効です。 次の表は、型をフィールドとしてマーシャリングするときの、文字列データ型のマーシャリングのオプションを示しています。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性は、文字列をフィールドにマーシャリングする <xref:System.Runtime.InteropServices.UnmanagedType> 列挙値を提供します。  
  
|列挙型|アンマネージ形式の説明|  
|----------------------|-------------------------------------|  
|`UnmanagedType.BStr`|長さと Unicode 文字がプレフィックスされた COM スタイル `BSTR`。|  
|`UnmanagedType.LPStr`|ANSI 文字の null で終わる配列へのポインター。|  
|`UnmanagedType.LPTStr`|プラットフォーム依存文字の null で終わる配列へのポインター。|  
|`UnmanagedType.LPWStr`|Unicode 文字の null で終わる配列へのポインター。|  
|`UnmanagedType.ByValTStr`|固定長の文字配列。配列の型は、包含構造体の文字セットによって決まります。|  
  
 `ByValTStr` 型は、構造体に定義されているインライン固定長文字配列で使用します。 その他の型は、文字列へのポインターを含む構造体に含まれている文字列参照に適用されます。  
  
 包含構造体に適用される <xref:System.Runtime.InteropServices.StructLayoutAttribute> 属性の `CharSet` 引数によって、構造体内の文字列の文字形式が決まります。 以下の構造体の例には、文字列参照とインライン文字列、そして ANSI、Unicode、およびプラットフォーム依存文字が含まれています。  
  
### <a name="type-library-representation"></a>タイプ ライブラリの表現  
  
```
struct StringInfoA {  
   char *    f1;  
   char      f2[256];  
};  
struct StringInfoW {  
   WCHAR *   f1;  
   WCHAR     f2[256];  
   BSTR      f3;  
};  
struct StringInfoT {  
   TCHAR *   f1;  
   TCHAR     f2[256];  
};  
```  
  
 次のコード例は、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して、同一の構造体を複数の異なる形式で定義する方法を示しています。  
  
```vb  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Ansi)> _  
Structure StringInfoA  
<MarshalAs(UnmanagedType.LPStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Unicode)> _  
Structure StringInfoW  
<MarshalAs(UnmanagedType.LPWStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
<MarshalAs(UnmanagedType.BStr)> Public f3 As String  
End Structure  
<StructLayout(LayoutKind.Sequential, CharSet := CharSet.Auto)> _  
Structure StringInfoT  
<MarshalAs(UnmanagedType.LPTStr)> Public f1 As String  
<MarshalAs(UnmanagedType.ByValTStr, SizeConst := 256)> _  
Public f2 As String  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Ansi)]  
struct StringInfoA {  
   [MarshalAs(UnmanagedType.LPStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Unicode)]  
struct StringInfoW {  
   [MarshalAs(UnmanagedType.LPWStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
   [MarshalAs(UnmanagedType.BStr)] public String f3;  
}  
[StructLayout(LayoutKind.Sequential, CharSet=CharSet.Auto)]  
struct StringInfoT {  
   [MarshalAs(UnmanagedType.LPTStr)] public String f1;  
   [MarshalAs(UnmanagedType.ByValTStr, SizeConst=256)] public String f2;  
}  
```  
  
<a name="cpcondefaultmarshalingforstringsanchor3"></a>   
## <a name="fixed-length-string-buffers"></a>固定長文字列バッファー  
 状況によっては、固定長の文字列バッファーを、操作するためにアンマネージ コードに渡す必要があります。 この場合、呼び出し先は渡されたバッファーの内容を修正できないので、単に文字列を渡すだけでは不十分です。 文字列が参照によって渡された場合でも、バッファーを特定のサイズに初期化する方法はありません。  
  
 この解決策は、<xref:System.Text.StringBuilder> バッファーを文字列ではなく引数として渡すことです。 呼び出し先は、`StringBuilder` の容量を超えない範囲で、`StringBuilder` を逆参照したり変更したりすることができます。 また、固定長に初期化することもできます。 たとえば、`StringBuilder` バッファーを初期化してその容量を `N` にする場合、マーシャラーは (`N`+1) 文字のサイズのバッファーを提供します。 +1 は、アンマネージ文字列に null 終了文字があることをしめしています。`StringBuilder` にはそれがありません。  
  
 たとえば、Microsoft Windows API `GetWindowText` (Windows.h に定義されている) 関数は、固定長の文字バッファーを操作するアンマネージド コードを渡す必要があります。 `LpString` は、呼び出し元が割り当てたサイズ `nMaxCount` のバッファーを示します。 呼び出し元は、バッファーを割り当てて、`nMaxCount` 引数を割り当てられたバッファーのサイズに設定することが期待されています。 次のコードは、Windows.h で定義されている `GetWindowText` 関数宣言を示しています。  
  
```  
int GetWindowText(  
HWND hWnd,        // Handle to window or control.  
LPTStr lpString,  // Text buffer.  
int nMaxCount     // Maximum number of characters to copy.  
);  
```  
  
 呼び出し先は、`StringBuilder` の容量を超えない範囲で、`StringBuilder` を逆参照したり変更したりすることができます。 次のコード例は、`StringBuilder` を固定長に初期化する方法を示しています。  
  
```vb  
Public Class Win32API  
Public Declare Auto Sub GetWindowText Lib "User32.Dll" _  
(h As Integer, s As StringBuilder, nMaxCount As Integer)  
End Class  
Public Class Window  
   Friend h As Integer ' Friend handle to Window.  
   Public Function GetText() As String  
      Dim sb As New StringBuilder(256)  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1)  
   Return sb.ToString()  
   End Function  
End Class  
```  
  
```csharp  
public class Win32API {  
[DllImport("User32.Dll")]  
public static extern void GetWindowText(int h, StringBuilder s,   
int nMaxCount);  
}  
public class Window {  
   internal int h;        // Internal handle to Window.  
   public String GetText() {  
      StringBuilder sb = new StringBuilder(256);  
      Win32API.GetWindowText(h, sb, sb.Capacity + 1);  
   return sb.ToString();  
   }  
}  
```  
  
## <a name="see-also"></a>関連項目
- [既定のマーシャリング動作](default-marshaling-behavior.md)
- [Blittable 型と非 Blittable 型](blittable-and-non-blittable-types.md)
- [方向属性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))
- [コピーと固定](copying-and-pinning.md)
