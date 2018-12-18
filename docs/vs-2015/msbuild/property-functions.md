---
title: Özellik işlevleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
caps.latest.revision: 35
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0194de0a9f14186dc02b17564c77b1b2bc7441be
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920199"
---
# <a name="property-functions"></a>Özellik İşlevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
.NET Framework sürüm 4 ve 4.5, MSBuild komut değerlendirilecek özellik işlevleri kullanılabilir. Özellik işlevleri özellikleri görünür her yerde kullanılabilir. Görevleri farklı özellik işlevleri hedefleri dışında kullanılabilir ve tüm hedef çalışmadan önce değerlendirilir.  
  
 MSBuild görevlerini kullanmadan, sistem saatini okuyabilir, dizeleri karşılaştırmak, normal ifadeleri eşleştirebilir ve derleme betiğinizin diğer eylemleri gerçekleştirin. MSBuild, dize ve numarası dizeye Dönüştür ve gerektiği gibi diğer dönüştürme yapmak çalışacaktır.  
  
 **Bu konuda:**  
  
-   [Özellik işlevi sözdizimi](#BKMK_Syntax)  
  
    -   [Dize özelliği işlevleri](#BKMK_String)  
  
    -   [Statik özellik işlevleri](#BKMK_Static)  
  
    -   [Statik özellikler örnek yöntemleri çağırma](#BKMK_InstanceMethods)  
  
    -   [MSBuild özellik işlevleri](#BKMK_PropertyFunctions)  
  
-   [İç içe özellik işlevleri](#BKMK_Nested)  
  
-   [MSBuild DoesTaskHostExist](#BKMK_DoesTaskHostExist)  
  
-   [MSBuild GetDirectoryNameOfFileAbove](#BKMK_GetDirectoryNameOfFileAbove)  
  
-   [MSBuild GetRegistryValue](#BKMK_GetRegistryValue)  
  
-   [MSBuild GetRegistryValueFromView](#BKMK_GetRegistryValueFromView)  
  
-   [MSBuild Makerelatıve](#BKMK_MakeRelative)  
  
-   [MSBuild ValueOrDefault](#BKMK_ValueOrDefault)  
  
##  <a name="BKMK_Syntax"></a> Özellik işlevi sözdizimi  
 Özellik işlevleri üç tür şunlardır; Her işlev, farklı bir sözdizimi vardır:  
  
-   Dize (örnek) özellik işlevleri  
  
-   Statik özellik işlevleri  
  
-   MSBuild özellik işlevleri  
  
###  <a name="BKMK_String"></a> Dize özelliği işlevleri  
 Tüm yapı özelliği yalnızca dize değerleri değerlerdir. Herhangi bir özelliğin üzerinde çalışılacak dize (örnek) yöntemlerini kullanabilirsiniz. Örneğin, bu kodu kullanarak tam yolu temsil eden bir yapı özelliğinden sürücü adı (ilk üç karakter) ayıklayın:  
  
 `$(ProjectOutputFolder.Substring(0,3))`  
  
###  <a name="BKMK_Static"></a> Statik özellik işlevleri  
 Derleme betiğinizin statik özelliklerine ve birçok sistem sınıfının yöntemlerine erişebilirsiniz. Statik bir özelliğin değerini almak için aşağıdaki sözdizimini kullanın burada *sınıfı* sistem sınıf adıdır ve *özelliği* özelliğin adıdır.  
  
 `$([Class]::Property)`  
  
 Örneğin, geçerli tarih ve saat için bir yapı özelliğini ayarlamak için aşağıdaki kodu kullanın.  
  
 `<Today>$([System.DateTime]::Now)</Today>`  
  
 Statik bir yöntemi çağırmak için aşağıdaki sözdizimini kullanın burada *sınıfı* sistem sınıfı adı *yöntemi* yöntemi adıdır ve *(Parametreler)* parametre listesi yöntem için:  
  
 `$([Class]::Method(Parameters))`  
  
 Örneğin, yeni bir GUID ile bir yapı özelliğini ayarlamak için bu betiği kullanabilirsiniz:  
  
 `<NewGuid>$([System.Guid]::NewGuid())</NewGuid>`  
  
 Statik özelliği işlevleri'nde herhangi bir statik yöntem veya özellik bu sistem sınıfların kullanabilirsiniz:  
  
- System.Byte  
  
- System.Char  
  
- System.Convert  
  
- System.DateTime  
  
- System.Decimal  
  
- System.Double  
  
- System.Enum  
  
- System.Guid  
  
- System.Int16  
  
- System.Int32  
  
- System.Int64  
  
- System.IO.Path  
  
- System.Math  
  
- System.UInt16  
  
- System.UInt32  
  
- System.UInt64  
  
- System.SByte  
  
- System.Single  
  
- System.String  
  
- System.StringComparer  
  
- System.TimeSpan  
  
- System.Text.RegularExpressions.Regex  
  
- Microsoft.Build.Utilities.ToolLocationHelper  
  
  Ayrıca, aşağıdaki statik yöntemleri ve özellikleri kullanabilirsiniz:  
  
- System.Environment::CommandLine  
  
- System.Environment::ExpandEnvironmentVariables  
  
- System.Environment::GetEnvironmentVariable  
  
- System.Environment::GetEnvironmentVariables  
  
- System.Environment::GetFolderPath  
  
- System.Environment::GetLogicalDrives  
  
- System.IO.Directory::GetDirectories  
  
- System.IO.Directory::GetFiles  
  
- System.IO.Directory::GetLastAccessTime  
  
- System.IO.Directory::GetLastWriteTime  
  
- System.IO.Directory::GetParent  
  
- System.IO.File::Exists  
  
- System.IO.File::GetCreationTime  
  
- System.IO.File::GetAttributes  
  
- System.IO.File::GetLastAccessTime  
  
- System.IO.File::GetLastWriteTime  
  
- System.IO.File::ReadAllText  
  
###  <a name="BKMK_InstanceMethods"></a> Statik özellikler örnek yöntemleri çağırma  
 Bir nesne örneğini döndüren statik özelliğe erişirse, o nesnenin örnek yöntemler çağırabilirsiniz. Bir örnek yöntemi çağırmak için aşağıdaki sözdizimini kullanın burada *sınıfı* sistem sınıfı adı *özelliği* özellik adı *yöntemi* adıdır yöntemi, ve *(Parametreler)* yöntem için parametre listesi:  
  
 `$([Class]::Property.Method(Parameters))`  
  
 Sınıfın adı, ad alanı ile tam olarak nitelenmiş olmalıdır.  
  
 Örneğin, geçerli tarihi bugün bir yapı özelliğini ayarlamak için aşağıdaki kodu kullanın.  
  
 `<Today>$([System.DateTime]::Now.ToString("yyyy.MM.dd"))</Today>`  
  
###  <a name="BKMK_PropertyFunctions"></a> MSBuild özellik işlevleri  
 Aritmetik, bit düzeyinde sağlamak için derleme çeşitli statik yöntemler erişilebilir mantıksal ve kaçış karakteri desteği. Aşağıdaki söz dizimini kullanarak bu yöntemlere erişmek burada *yöntemi* yöntemi adıdır ve *parametreleri* yöntem için parametre listesi.  
  
 `$([MSBuild]::Method(Parameters))`  
  
 Örneğin, birlikte sayısal değerlere sahip iki özellik eklemek için aşağıdaki kodu kullanın.  
  
 `$([MSBuild]::Add($(NumberOne), $(NumberTwo))`  
  
 MSBuild özellik işlevlerin bir listesi aşağıda verilmiştir:  
  
|İşlev imzası|Açıklama|  
|------------------------|-----------------|  
|çift (double double b) Ekle|İki çiftten ekleyin.|  
|uzun süre (uzun uzun a, b) Ekle|İki Integer ekleyin.|  
|çift (double double b) çıkarma|İki çiftten çıkarın.|  
|uzun süre (uzun uzun a, b) çıkarma|İki Integer çıkarın.|  
|çift (double double b) çarpın.|İki çiftten çarpın.|  
|uzun süre (uzun uzun b) çarpın.|İki Integer çarpın.|  
|çift (double double b) Böl|İki çiftten bölün.|  
|uzun süre (uzun uzun b) Böl|İki Integer bölün.|  
|çift (double double b) mod|İki çiftten.|  
|uzun süre (uzun uzun b)|İki Integer.|  
|dize Escape(string unescaped)|MSBuild kaçış kurallara göre dize çıkış.|  
|Unescape (Atlanan dizesini) dize|MSBuild kaçış kurallara göre dize unescape.|  
|int BitwiseOr (int ilk, int saniye)|Bit düzeyinde gerçekleştirmek `OR` ilk ve ikinci (ilk &#124; ikinci).|  
|int BitwiseAnd (int ilk, int saniye)|Bit düzeyinde gerçekleştirmek `AND` ilk ve (ilk ve ikinci) saniye.|  
|int BitwiseXor (int ilk, int saniye)|Bit düzeyinde gerçekleştirmek `XOR` ilk ve ikinci (ilk ^ ikinci).|  
|int BitwiseNot(int first)|Bit düzeyinde gerçekleştirmek `NOT` (~ ilk).|  
  
##  <a name="BKMK_Nested"></a> İç içe özellik işlevleri  
 Özellik işlevleri aşağıdaki örnekte gösterildiği gibi daha karmaşık, işlev forma birleştirebilirsiniz.  
  
 `$([MSBuild]::BitwiseAnd(32,   $([System.IO.File]::GetAttributes(tempFile))))`  
  
 Bu örnekte değerini döndürür <xref:System.IO.FileAttributes> `Archive` bit (32 ya da 0) yolu tarafından belirtilen dosyanın `tempFile`. Numaralandırılmış veri değerlerini özelliği işlevlerdeki adıyla görünemez dikkat edin. Sayısal değer (32) bunun yerine kullanılmalıdır.  
  
 Meta veri özellik iç içe geçmiş işlevlerde de görünebilir. Daha fazla bilgi için [toplu işleme](../msbuild/msbuild-batching.md).  
  
##  <a name="BKMK_DoesTaskHostExist"></a> MSBuild DoesTaskHostExist  
 `DoesTaskHostExist` MSBuild özelliği işlevinde bir görev ana bilgisayarı için belirtilen çalışma zamanı ve mimari değerleri yüklü olup olmadığını döndürür.  
  
 Bu özellik işlev sözdizimi aşağıdaki gibidir:  
  
```  
$[MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture)  
```  
  
##  <a name="BKMK_GetDirectoryNameOfFileAbove"></a> MSBuild GetDirectoryNameOfFileAbove  
 MSBuild `GetDirectoryNameOfFileAbove` özelliği işlevi, bir dosya yolunda geçerli dizinin üzerindeki dizinlerde arar.  
  
 Bu özellik işlev sözdizimi aşağıdaki gibidir:  
  
```  
$[MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile)  
```  
  
 Aşağıdaki kod, bu sözdizimini örneğidir.  
  
```  
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />  
```  
  
##  <a name="BKMK_GetRegistryValue"></a> MSBuild GetRegistryValue  
 MSBuild `GetRegistryValue` özelliği işlevi bir kayıt defteri anahtarı değerini döndürür. Bu işlev, iki bağımsız değişkeni, anahtar adı ve değeri adını alır ve kayıt defterinden değeri döndürür. Değer adı belirtmezseniz, varsayılan değer döndürülür.  
  
 Aşağıdaki örnekler, bu işlevin nasıl kullanıldığını açıklar:  
  
```  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value  
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))  
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value  
  
```  
  
##  <a name="BKMK_GetRegistryValueFromView"></a> MSBuild GetRegistryValueFromView  
 MSBuild `GetRegistryValueFromView` özelliği işlevi alır sistem kayıt defteri verilerini verilen kayıt defteri anahtarı, değer ve bir veya daha fazla kayıt görünümleri sıralı. Bunlar bulunmayana kadar sırayla her bir kayıt defteri görünümü'nde anahtar ve değer aranır.  
  
 Bu özelliği işlevi için sözdizimi aşağıdaki gibidir:  
  
 [MSBuild\]:: GetRegistryValueFromView (dize keyName, dize valueName, nesne defaultValue, params nesne [] görünümleri)  
  
 Windows 64-bit işletim sistemi 32-bit uygulamalar için bir HKEY_LOCAL_MACHINE\Software kayıt defteri görünümü sunan bir HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node kayıt defteri anahtarı korur.  
  
 Varsayılan olarak, 32 bitlik bir uygulama WOW64 üzerinde çalışan 32-bit kayıt defteri görünümü erişir ve 64 bitlik bir uygulama 64-bit kayıt defteri görünümü erişir.  
  
 Aşağıdaki kayıt defteri görünümleri kullanılabilir:  
  
|Kayıt defteri görünümü|Tanım|  
|-------------------|----------------|  
|RegistryView.Registry32|32 bit uygulama kayıt defteri görünümü.|  
|RegistryView.Registry64|Uygulama 64-bit kayıt defteri görünümü.|  
|RegistryView.Default|Uygulamanın üzerinde çalıştığı işlem eşleşen kayıt defteri görünümü.|  
  
 Bir örnek verilmiştir.  
  
 `$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))`  
  
 64-bit kayıt defteri görünümü ve ardından 32-bit kayıt defteri görünümü ilk bakarak Referenceassembly'ler anahtarının SLRuntimeInstallPath verilerini alır.  
  
##  <a name="BKMK_MakeRelative"></a> MSBuild Makerelatıve  
 MSBuild `MakeRelative` özelliği işlevi ilk yol göreli ikinci yol göreli yolunu döndürür. Her yol, dosya veya klasör olabilir.  
  
 Bu özellik işlev sözdizimi aşağıdaki gibidir:  
  
```  
$[MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2))  
```  
  
 Aşağıdaki kod, bu sözdizimini örneğidir.  
  
```xml  
<PropertyGroup>  
    <Path1>c:\users\</Path1>  
    <Path2>c:\users\username\</Path2>  
</PropertyGroup>  
  
<Target Name = "Go">  
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />  
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />  
</Target>  
  
<!--  
Output:  
   username\  
   ..\  
-->  
```  
  
##  <a name="BKMK_ValueOrDefault"></a> MSBuild ValueOrDefault  
 MSBuild `ValueOrDefault` özelliği işlevi, null veya boş değilse ilk bağımsız değişkeni döndürür. İlk bağımsız değişken null veya boş ise, işlev, ikinci bağımsız değişkeni döndürür.  
  
 Aşağıdaki örnek, bu işlevin nasıl kullanıldığını gösterir.  
  
```  
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>  
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>  
    </PropertyGroup>  
  
    <Target Name="MyTarget">  
        <Message Text="Value1 = $(Value1)" />  
        <Message Text="Value2 = $(Value2)" />  
    </Target>  
</Project>  
  
<!--  
Output:   
  Value1 = a  
  Value2 = b  
-->  
```

## <a name="see-also"></a>Ayrıca Bkz.
[MSBuild özellikleri](msbuild-properties1.md)   
[MSBuild'e genel bakış](msbuild.md)


