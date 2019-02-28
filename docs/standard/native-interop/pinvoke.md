---
title: プラットフォーム呼び出し (P/Invoke)
description: .NET で P/Invoke を介してネイティブ関数を呼び出す方法について説明します。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 51026eab92ae4fd47ccdd78321be21bdbb5ecf49
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981258"
---
# <a name="platform-invoke-pinvoke"></a>プラットフォーム呼び出し (P/Invoke)

P/Invoke は、アンマネージド ライブラリ内の構造体、コールバック、および関数をマネージド コードからアクセスできるようにするテクノロジです。 P/Invoke API のほとんどは、`System` と `System.Runtime.InteropServices` の 2 つの名前空間に含まれます。 これら 2 つの名前空間を使用すると、ネイティブ コンポーネントと通信する方法を記述するツールを利用できます。

最も一般的な例から始めましょう。これはマネージド コードでアンマネージド 関数を呼び出します。 コマンドライン アプリケーションからメッセージ ボックスを表示してみましょう。

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

上の例は単純ですが、マネージド コードからアンマネージド 関数を呼び出すために必要なことを示しています。 この例の手順を説明します。

*   1 行目は、必要なすべての項目を保持する名前空間 `System.Runtime.InteropServices` のステートメントの使用を示しています。
*   7 行目で `DllImport` 属性を導入しています。 この属性は、ランタイムにアンマネージ DLL を読み込むように伝えるため、きわめて重要です。 渡された文字列は、ターゲット関数が入っている DLL です。
*   8 行目は、P/Invoke 作業の最も重要な箇所です。 ここでは、アンマネージドと**正確に同じシグネチャ**を持つマネージド メソッドを定義しています。 宣言には新しいキーワード `extern` があることがわかります。これはランタイムに、これが外部メソッドであり、それを呼び出したときに、ランタイムが `DllImport` 属性に指定された DLL からそれを見つける必要があることを伝えます。

例の残りの部分は、その他のマネージド メソッドと同じように、メソッドを呼び出しているだけです。

サンプルは、macOS の場合も似ています。 macOS ではダイナミック ライブラリの名前付けのスキームが異なるため、`DllImport` 属性内のライブラリの名前を変更する必要があります。 次のサンプルでは、`getpid(2)` 関数を使用して、アプリケーションのプロセス ID を取得し、それをコンソールに出力しています。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libSystem shared library and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

これは Linux でも同様です。 `getpid(2)` は標準的な [POSIX](https://en.wikipedia.org/wiki/POSIX) システム コールであるため、関数名が同じです。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc shared library and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

## <a name="invoking-managed-code-from-unmanaged-code"></a>アンマネージド コードからのマネージド コードの呼び出し

ランタイムは通信が双方向にフローする通信を許可しているため、関数ポインターを使用して、ネイティブ関数からマネージド コードをコール バックすることができます。 マネージド コードで、関数ポインターに最も近いものが、**デリゲート**であるため、これをネイティブ コードからマネージド コードへのコールバックを許可するために使います。

この機能を使用する方法は、前述のマネージドからネイティブへのプロセスに似ています。 指定されたコールバックに対し、ユーザーがシグネチャと一致するデリゲートを定義し、それを外部メソッドに渡します。 ランタイムは、他のすべてのことを処理します。

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

例の手順に従う前に、使用する必要があるアンマネージ関数のシグネチャについて見直しておくのはよいことです。 すべてのウィンドウを列挙するために呼び出す関数は、次のシグネチャを持ちます。`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`

最初のパラメーターでは、コールバックです。 上記のコールバックのシグネチャは次のとおりです。`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`

次の例を確認してみましょう。

*   例の 9 行目では、アンマネージ コードからのコールバックのシグネチャと一致するデリゲートを定義しています。 マネージド コードで `IntPtr` を使用して、LPARAM および HWND 型を表す方法に注意してください。
*   13 行目と 14 行目では、user32.dll ライブラリから `EnumWindows` 関数を導入しています。
*   17 - 20 行目は、デリゲートを実装しています。 この簡単な例では、ハンドルだけコンソールに出力します。
*   最後に、24 行目で、外部メソッドを呼び出し、デリゲートを渡しています。

Linux と macOS の例を、以下に示します。 それらの場合、`libc` C ライブラリに見つかる `ftw` 関数を使用します。 この関数は、ディレクトリ階層をスキャンするために使用し、そのパラメーターの 1 つとして、関数へのポインターを受け取ります。 上記のメソッドのシグネチャは次のとおりです。`int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

macOS の例では、同じ関数を使用していますが、唯一の違いは `DllImport` 属性への引数です。macOS は `libc` を別の場所で保持しているためです。

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

前述の例のどちらも、パラメーターに依存し、どちらの場合もパラメーターは、マネージド型として指定されています。 ランタイムは、"正しいこと" を実行し、これらを他方の側で同等のものに処理します。 型をネイティブ コードにマーシャリングする方法については、「[Type marshalling (型のマーシャリング)](type-marshalling.md)」を参照してください。


## <a name="more-resources"></a>その他のリソース

*   [PInvoke.net wiki](https://www.pinvoke.net/) は、一般的な Win32 API とそれらを呼び出す方法に関する情報を記載した優れた Wiki です。
*   [MSDN の P/Invoke](/cpp/dotnet/native-and-dotnet-interoperability)
*   [P/invoke に関する Mono のドキュメント](https://www.mono-project.com/docs/advanced/pinvoke/)
