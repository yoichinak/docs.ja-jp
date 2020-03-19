---
title: バイナリ シリアル化
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.openlocfilehash: 9df9b73a1a1347b952d76b76c9058578f5e9f401
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401269"
---
# <a name="binary-serialization"></a>バイナリ シリアル化

シリアル化は、オブジェクトの状態をストレージ メディアに格納するプロセスとして定義することができます。 このプロセスの実行中に、オブジェクトのパブリックおよびプライベートなフィールドとクラス (クラスを格納しているアセンブリを含む) の名前がバイト ストリームに変換され、データ ストリームに書き込まれます。 続いてオブジェクトが逆シリアル化され、元のオブジェクトの完全な複製が作成されます。

オブジェクト指向環境でシリアル化機構を実装する場合は、使いやすさと柔軟性の間での数多くのトレードオフについて考慮する必要があります。 プロセスを十分に制御できる場合は、プロセスの大部分を自動化できます。 たとえば、単純なバイナリ シリアル化では不十分な状況が発生する場合や、シリアル化が必要なクラス内のフィールドを決定するだけの明確な理由がある場合があります。 以下のセクションでは、.NET に用意されている堅牢なシリアル化機構について検討し、必要に応じてプロセスをカスタマイズするためのいくつかの重要な機能について説明します。

> [!NOTE]
> オブジェクトのシリアル化と逆シリアル化を行う際に使用した .NET Framework のバージョンが異なる場合、UTF-8 または UTF-7 でエンコードされたオブジェクトの状態は保持されません。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

バイナリ シリアル化を使用すると、オブジェクト内のプライベート メンバーを変更できるため、その状態を変更できます。 このため、パブリック API サーフェスで動作する<xref:System.Text.Json?displayProperty=fullName>他のシリアル化フレームワーク (など) をお勧めします。

## <a name="net-core"></a>.NET Core

.NET Core では、型のサブセットに対してバイナリ シリアル化がサポートされています。 サポートされている型の一覧については、次の[「シリアル化可能な型](#serializable-types)」セクションを参照してください。 ここに示されている型は、.NET Framework 4.5.1 以降のバージョン間、および .NET Core 2.0 以降のバージョン間でシリアル化できることが保証されています。 Mono などの他の .NET 実装は公式にはサポートされていませんが、動作する必要があります。

### <a name="serializable-types"></a>シリアル化可能な型

> [!div class="mx-tdCol2BreakAll"]
> | Type | Notes |
> | - | - |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.AccessViolationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.AggregateException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ApplicationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ArgumentException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ArgumentNullException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ArithmeticException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Array?displayProperty=nameWithType> | |
> | <xref:System.ArraySegment%601?displayProperty=nameWithType> | |
> | <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Attribute?displayProperty=nameWithType> | |
> | <xref:System.BadImageFormatException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Boolean?displayProperty=nameWithType> | |
> | <xref:System.Byte?displayProperty=nameWithType> | |
> | <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Char?displayProperty=nameWithType> | |
> | <xref:System.Collections.ArrayList?displayProperty=nameWithType> | |
> | <xref:System.Collections.BitArray?displayProperty=nameWithType> | |
> | <xref:System.Collections.Comparer?displayProperty=nameWithType> | |
> | <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Hashtable?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType> | |
> | <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType> | |
> | <xref:System.Collections.Queue?displayProperty=nameWithType> | |
> | <xref:System.Collections.SortedList?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType> | |
> | <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType> | |
> | <xref:System.Collections.Stack?displayProperty=nameWithType> | |
> | `System.Collections.Generic.NonRandomizedStringEqualityComparer` | NET コア 2.0.4 から始まります。 |
> | <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType> | |
> | <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。<br/>.NET Framework から .NET Core へのシリアル化はサポートされていません。 |
> | <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ContextMarshalException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DBNull?displayProperty=nameWithType> | NET Core 2.0.2 以降のバージョンから開始します。 |
> | <xref:System.Data.Common.DbException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.ConstraintException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.DataException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.DataSet?displayProperty=nameWithType> | |
> | <xref:System.Data.DataTable?displayProperty=nameWithType> | に`RemotingFormat``SerializationFormat.Binary`設定した場合、.NET Core 2.1 以降のバージョンとのみ交換できます。 |
> | <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.EvaluateException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.PropertyCollection?displayProperty=nameWithType> | |
> | <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。<br/>.NET Framework から .NET Core へのシリアル化はサポートされていません |
> | <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType> | |
> | <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.StrongTypingException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DataMisalignedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DateTime?displayProperty=nameWithType> | |
> | <xref:System.DateTimeOffset?displayProperty=nameWithType> | |
> | <xref:System.Decimal?displayProperty=nameWithType> | |
> | `System.Diagnostics.Contracts.ContractException` | NET コア 2.0.4 から始まります。 |
> | <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DivideByZeroException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.DllNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Double?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Color?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Point?displayProperty=nameWithType> | |
> | <xref:System.Drawing.PointF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Rectangle?displayProperty=nameWithType> | |
> | <xref:System.Drawing.RectangleF?displayProperty=nameWithType> | |
> | <xref:System.Drawing.Size?displayProperty=nameWithType> | |
> | <xref:System.Drawing.SizeF?displayProperty=nameWithType> | |
> | <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Enum?displayProperty=nameWithType> | |
> | <xref:System.EventArgs?displayProperty=nameWithType> | NET コア 2.0.6 から始まります。 |
> | <xref:System.Exception?displayProperty=nameWithType> | |
> | <xref:System.ExecutionEngineException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.FieldAccessException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.FormatException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Globalization.CompareInfo?displayProperty=nameWithType> | |
> | <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Globalization.SortVersion?displayProperty=nameWithType> | |
> | <xref:System.Guid?displayProperty=nameWithType> | |
> | `System.IO.Compression.ZLibException` | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.FileFormatException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.FileLoadException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.IOException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.InvalidDataException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IO.PathTooLongException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.InsufficientMemoryException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Int16?displayProperty=nameWithType> | |
> | <xref:System.Int32?displayProperty=nameWithType> | |
> | <xref:System.Int64?displayProperty=nameWithType> | |
> | <xref:System.IntPtr?displayProperty=nameWithType> | |
> | <xref:System.InvalidCastException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.InvalidOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.InvalidProgramException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.MemberAccessException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.MethodAccessException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.MissingFieldException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.MissingMemberException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.MissingMethodException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.Cookie?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieCollection?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieContainer?displayProperty=nameWithType> | |
> | <xref:System.Net.CookieException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.HttpListenerException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.WebException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.NotFiniteNumberException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.NotImplementedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.NotSupportedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.NullReferenceException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Nullable%601?displayProperty=nameWithType> | |
> | <xref:System.Numerics.BigInteger?displayProperty=nameWithType> | |
> | <xref:System.Numerics.Complex?displayProperty=nameWithType> | |
> | <xref:System.Object?displayProperty=nameWithType> | |
> | <xref:System.ObjectDisposedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.OperationCanceledException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.OutOfMemoryException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.OverflowException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.RankException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。<br/>.NET Framework から .NET Core へのシリアル化はサポートされていません。 |
> | <xref:System.Reflection.TargetException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.SByte?displayProperty=nameWithType> | |
> | <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.HostProtectionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.SecurityException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。<br/>限定されたシリアル化データ。 |
> | <xref:System.Security.VerificationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Single?displayProperty=nameWithType> | |
> | <xref:System.StackOverflowException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.String?displayProperty=nameWithType> | |
> | <xref:System.StringComparer?displayProperty=nameWithType> | |
> | <xref:System.SystemException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Text.StringBuilder?displayProperty=nameWithType> | |
> | <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.TimeSpan?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneInfo?displayProperty=nameWithType> | |
> | <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.TimeoutException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Transactions.TransactionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Tuple?displayProperty=nameWithType> | |
> | <xref:System.TypeAccessException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.TypeInitializationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.TypeLoadException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.TypeUnloadedException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.UInt16?displayProperty=nameWithType> | |
> | <xref:System.UInt32?displayProperty=nameWithType> | |
> | <xref:System.UInt64?displayProperty=nameWithType> | |
> | <xref:System.UIntPtr?displayProperty=nameWithType> | |
> | <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Uri?displayProperty=nameWithType> | |
> | <xref:System.UriFormatException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.ValueTuple?displayProperty=nameWithType> | .NET Framework 4.7 以前のバージョンではシリアル化できません。 |
> | <xref:System.ValueType?displayProperty=nameWithType> | |
> | <xref:System.Version?displayProperty=nameWithType> | |
> | <xref:System.WeakReference%601?displayProperty=nameWithType> | |
> | <xref:System.WeakReference?displayProperty=nameWithType> | |
> | <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Xml.XmlException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |
> | <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> | NET コア 2.0.4 から始まります。 |

## <a name="see-also"></a>関連項目

- <xref:System.Runtime.Serialization>\
オブジェクトのシリアル化と逆シリアル化に使用できるクラスが含まれています。

- [XML および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)\
共通言語ランタイムに付属している XML シリアル化機構について説明します。

- [セキュリティとシリアル化](../../../docs/framework/misc/security-and-serialization.md)\
シリアル化を実行するコードを記述する際に従う必要がある、安全なコーディングのガイドラインについて説明します。

- [NET リモート処理](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))\
リモート通信用の .NET Framework で開始するさまざまな方法について説明します。

- [ASP.NETおよび XML Web サービス クライアントを使用して作成される XML Web サービス](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7bkzywba(v=vs.100))\
ASP.NETを使用して作成された XML Web サービスをプログラミングする方法について説明する記事です。
