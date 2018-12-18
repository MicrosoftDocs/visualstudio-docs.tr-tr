---
title: '&lt;InstallChecks&gt; öğesi (Önyükleyici) | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <InstallChecks> element [bootstrapper]
ms.assetid: ad329c87-b0ad-4304-84de-ae9496514c42
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 03f489c22c8912e332f7d01e6ec4ac48aacda30b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891082"
---
# <a name="ltinstallchecksgt-element-bootstrapper"></a>&lt;InstallChecks&gt; öğesi (Önyükleyici)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`InstallChecks` Öğesinin desteklediği tüm uygulama için uygun önkoşulların yüklendiğinden emin olmak için yerel bilgisayara karşı testler çeşitli başlatılıyor.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
<InstallChecks>  
    <AssemblyCheck   
        Property  
        Name  
        PublicKeyToken  
        Version  
        Language  
        ProcessorArchitecture  
    />  
    <RegistryCheck  
        Property  
        Key  
        Value  
    />  
    <ExternalCheck   
        PackageFile  
        Property  
        Arguments  
    />  
    <FileCheck   
        Property  
        FileName  
        SearchPath  
        SpecialFolder  
        SearchDepth  
    />  
    <MsiProductCheck   
        Property  
        Product  
        Feature  
    />  
    <RegistryFileCheck   
        Property  
        Key  
        Value  
        FileName  
        SearchDepth  
    />  
</InstallChecks>  
```  
  
## <a name="assemblycheck"></a>AssemblyCheck  
 Bu öğe isteğe bağlı alt öğesidir `InstallChecks`. Her örneği için `AssemblyCheck`, önyükleyici öğe tarafından belirtilen derleme genel derleme önbelleğinde (GAC) mevcut olduğundan emin olun. Hiçbir öğe içeren ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sonucu depolamak için özellik adı. Bu özellik, bir test başvurulabilir `InstallConditions` bir alt öğesi olan `Command` öğesi. Daha fazla bilgi için [ \<komutları > öğesi](../deployment/commands-element-bootstrapper.md).|  
|`Name`|Gerekli. Denetlenecek bütünleştirilmiş kodun tam adı.|  
|`PublicKeyToken`|Gerekli. Kısaltılmış formun ortak anahtarın bu kesin adlı derleme ile ilişkili. Tüm derlemeler GAC içinde depolanan bir adı, sürümü ve bir ortak anahtar olmalıdır.|  
|`Version`|Gerekli. Derleme sürümü.<br /><br /> Sürüm numarası şu biçimdedir \< *ana sürüm*>.\< *podverze*>.\< *derleme sürümü*>.\< *düzeltme sürümü*>.|  
|`Language`|İsteğe bağlı. Yerelleştirilmiş bir derleme dili. Varsayılan değer `neutral`.|  
|`ProcessorArchitecture`|İsteğe bağlı. Bu yükleme tarafından hedeflenen bilgisayarı işlemcisini. Varsayılan değer `msil`.|  
  
## <a name="externalcheck"></a>ExternalCheck  
 Bu öğe isteğe bağlı alt öğesidir `InstallChecks`. Her örneği için `ExternalCheck`, önyükleyici isimlendirilmiş harici program ayrı bir işlemde yürütür ve çıkış kodu tarafından belirtilen özellik depolar `Property`. `ExternalCheck` karmaşık bağımlılık denetimlerini uygulamak için veya bir bileşenin varlığını denetlemek için tek yolu, örneği olduğunda yararlıdır.  
  
 `ExternalCheck` hiçbir öğe içeren ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sonucu depolamak için özellik adı. Bu özellik, bir test başvurulabilir `InstallConditions` bir alt öğesi olan `Command` öğesi. Daha fazla bilgi için [ \<komutları > öğesi](../deployment/commands-element-bootstrapper.md).|  
|`PackageFile`|Gerekli. Yürütmek için dış program. Programın Kurulum dağıtım paketinin bir parçası olmalıdır.|  
|`Arguments`|İsteğe bağlı. Yürütülebilir dosya tarafından adlandırılan komut satırı bağımsız değişkenleri sağlayan `PackageFile`.|  
  
## <a name="filecheck"></a>FileCheck  
 Bu öğe isteğe bağlı alt öğesidir `InstallChecks`. Her örneği için `FileCheck`, önyükleyici adlandırılmış dosyanın var olduğundan ve dosyanın sürüm numarasını döndürür olup olmadığını belirler. Dosya bir sürüm numarasına sahip değilse, önyükleyici tarafından adlandırılan özelliği ayarlar `Property` 0. Dosya mevcut değilse `Property` herhangi bir değere ayarlı değil.  
  
 `FileCheck` hiçbir öğe içeren ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sonucu depolamak için özellik adı. Bu özellik, bir test başvurulabilir `InstallConditions` bir alt öğesi olan `Command` öğesi. Daha fazla bilgi için [ \<komutları > öğesi](../deployment/commands-element-bootstrapper.md).|  
|`FileName`|Gerekli. Bulunacak dosya adı.|  
|`SearchPath`|Gerekli. Disk veya dosyayı aramak bir klasör. Bu göreli bir yol olmalıdır `SpecialFolder` atanır; Aksi takdirde, mutlak bir yol olmalıdır.|  
|`SpecialFolder`|İsteğe bağlı. Windows veya çok özel anlamlı olan bir klasörü [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. Yorumlamak için varsayılandır `SearchPath` mutlak bir yol olarak. Geçerli değerler şunlardır:<br /><br /> `AppDataFolder`. Bu uygulama veri klasörü [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] uygulama; geçerli kullanıcının belirli.<br /><br /> `CommonAppDataFolder`. Tüm kullanıcılar tarafından kullanılan uygulama veri klasörü.<br /><br /> `CommonFilesFolder`. Geçerli kullanıcı için ortak dosyalar klasörü.<br /><br /> `LocalDataAppFolder`. Gezici olmayan uygulamalar için veri klasörü.<br /><br /> `ProgramFilesFolder`. 32-bit uygulamalar için standart Program dosyaları klasörü.<br /><br /> `StartUpFolder`. Sistem başlangıçta başlatılan tüm uygulamalara içeren klasör.<br /><br /> `SystemFolder`. 32-bit sistem DLL içeren klasör.<br /><br /> `WindowsFolder`. Windows sistemi yüklemesi içeren klasör.<br /><br /> `WindowsVolume`. Sürücü veya Windows sistemi yüklemesi içeren bölümü.|  
|`SearchDepth`|İsteğe bağlı. Derinliğinde adlandırılmış dosya alt klasörleri aramak istediğiniz. Arama derinliği öncelikli olur. Varsayılan arama tarafından belirtilen en üst düzey klasör sınırlar 0 ' dır `SpecialFolder` ve **SearchPath**.|  
  
## <a name="msiproductcheck"></a>MsiProductCheck  
 Bu öğe isteğe bağlı alt öğesidir `InstallChecks`. Her örneği için `MsiProductCheck`, önyükleyici belirtilen Microsoft Windows Installer yükleme tamamlanana kadar çalıştırıldı olup olmadığını denetler. Özellik değeri, yüklü bir ürün durumuna bağlı olarak ayarlanır. Ürününün yüklü olduğu, pozitif bir değer belirtir. 0 veya -1'de gösterir, yüklü değil. (Lütfen Windows Installer SDK MsiQueryFeatureState daha fazla bilgi için bkz.) . Windows Installer bilgisayarda yüklü değilse `Property` ayarlı değil.  
  
 `MsiProductCheck` hiçbir öğe içeren ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sonucu depolamak için özellik adı. Bu özellik, bir test başvurulabilir `InstallConditions` bir alt öğesi olan `Command` öğesi. Daha fazla bilgi için [ \<komutları > öğesi](../deployment/commands-element-bootstrapper.md).|  
|`Product`|Gerekli. Yüklü ürüne GUİD'i.|  
|`Feature`|İsteğe bağlı. Yüklenen uygulamanın belirli bir özellik için GUID.|  
  
## <a name="registrycheck"></a>RegistryCheck  
 Bu öğe isteğe bağlı alt öğesidir `InstallChecks`. Her örneği için `RegistryCheck`, önyükleyici belirtilen kayıt defteri anahtarının var olup var veya belirtilen değer olup olmadığını denetler.  
  
 `RegistryCheck` hiçbir öğe içeren ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sonucu depolamak için özellik adı. Bu özellik, bir test başvurulabilir `InstallConditions` bir alt öğesi olan `Command` öğesi. Daha fazla bilgi için [ \<komutları > öğesi](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Gerekli. Kayıt defteri anahtarı adı.|  
|`Value`|İsteğe bağlı. Alınacak kayıt defteri değeri adı. Varsayılan değer metninin döndürmek için varsayılandır. `Value` bir dize veya bir DWORD olması gerekir.|  
  
## <a name="registryfilecheck"></a>RegistryFileCheck  
 Bu öğe isteğe bağlı alt öğesidir `InstallChecks`. Her örneği için `RegistryFileCheck`, önyükleyici ilk yol, dosyayı belirtilen kayıt defteri anahtarından almaya çalışırken belirtilen dosya sürümünü alır. Kayıt defterinde bir değer olarak belirtilen bir dizindeki bir dosya aramak istiyorsanız bu özellikle yararlıdır.  
  
 `RegistryFileCheck` hiçbir öğe içeren ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sonucu depolamak için özellik adı. Bu özellik, bir test başvurulabilir `InstallConditions` bir alt öğesi olan `Command` öğesi. Daha fazla bilgi için [ \<komutları > öğesi](../deployment/commands-element-bootstrapper.md).|  
|`Key`|Gerekli. Kayıt defteri anahtarı adı. Değeri olarak bir dosya yolu sürece yorumlanır `File` özniteliği. Bu anahtar yoksa `Property` ayarlı değil.|  
|`Value`|İsteğe bağlı. Alınacak kayıt defteri değeri adı. Varsayılan değer metninin döndürmek için varsayılandır. `Value` bir dize olmalıdır.|  
|`FileName`|İsteğe bağlı. Bir dosya adı. Belirtilmişse alınan kayıt defteri anahtarından değer bir dizin yolu olarak kabul edilir ve bu ad, kendisine eklenir. Belirtilmezse, kayıt defterinden döndürülen değer tam yolu bir dosya olduğu varsayılır.|  
|`SearchDepth`|İsteğe bağlı. Derinliğinde adlandırılmış dosya alt klasörleri aramak istediğiniz. Arama derinliği öncelikli olur. Varsayılan arama kayıt defteri anahtarının değeri tarafından belirtilen en üst düzey klasör kısıtlayan 0 ' dır.|  
  
## <a name="remarks"></a>Açıklamalar  
 Altındaki öğeler `InstallChecks` çalıştırılan testleri tanımlayın, bunları yürütülmez. Testleri yürütmek için oluşturmalısınız `Command` öğeleri altında `Commands` öğesi.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde `InstallChecks` öğesi için ürün dosyasında kullanılan [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
```  
<InstallChecks>  
    <ExternalCheck Property="DotNetInstalled" PackageFile="dotnetchk.exe" />  
    <RegistryCheck Property="IEVersion" Key="HKLM\Software\Microsoft\Internet Explorer" Value="Version" />  
</InstallChecks>  
```  
  
## <a name="installconditions"></a>InstallConditions  
 Zaman `InstallChecks` olan değerlendirilir, bunlar özellikleri oluşturmak. Özellikleri tarafından kullanılan `InstallConditions` bir paket yükleyin, atlama, başarısız veya belirlemek için. Aşağıdaki tabloda `InstallConditions`:  
  
|||  
|-|-|  
|`FailIf`|Varsa `FailIf` koşul true olarak değerlendirilir, paket başarısız olur. Koşulların geri kalanını değerlendirilmez.|  
|`BypassIf`|Varsa `BypassIf` koşul true olarak değerlendirilir, paket atlanır. Koşulların geri kalanını değerlendirilmez.|  
  
## <a name="predefined-properties"></a>Önceden tanımlanmış özellikler  
 Aşağıdaki tabloda `BypassIf` ve `FailIf` öğeleri:  
  
|Özellik|Notlar|Olası değerler|  
|--------------|-----------|---------------------|  
|`Version9X`|Windows 9 X işletim sistemi sürüm numarası.|4.10 Windows 98 =|  
|`VersionNT`|Windows NT tabanlı bir işletim sistemi sürüm numarası.|Major.Minor.ServicePack<br /><br /> 5.0 Windows 2000 =<br /><br /> 5.1.0 Windows XP =<br /><br /> 5.1.2 Windows XP Professional SP2 =<br /><br /> 5.2.0 Windows Server 2003 =|  
|`VersionNT64`|64 bit Windows NT tabanlı bir işletim sistemi sürüm numarası.|Aynı daha önce bahsedilen.|  
|`VersionMsi`|Windows Installer hizmeti sürüm numarası.|2.0 Windows Installer 2.0 =|  
|`AdminUser`|Bir kullanıcının Windows NT tabanlı bir işletim sistemi üzerinde yönetici ayrıcalıklarına sahip olup olmadığını belirtir.|0 = yönetici ayrıcalığı yok<br /><br /> 1 = yönetici ayrıcalıkları|  
  
 Örneğin, Windows 95 çalıştıran bir bilgisayara yükleme engellemek için aşağıdaki gibi bir kod kullanın:  
  
```  
<!-- Block install on Windows 95 -->  
    <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatform"/>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<Komutları > öğesi](../deployment/commands-element-bootstrapper.md)   
 [Ürün ve Paket Şema Başvurusu](../deployment/product-and-package-schema-reference.md)



