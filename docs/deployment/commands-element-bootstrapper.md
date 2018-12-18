---
title: '&lt;Komutları&gt; öğesi (Önyükleyici) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <Commands> element [bootstrapper]
ms.assetid: e61d5787-fe1f-4ebf-b0cf-0d7909be7ffb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 785df23b3d76573182eeb97efc5b359e7298a009
ms.sourcegitcommit: 8ee7efb70a1bfebcb6dd9855b926a4ff043ecf35
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/17/2018
ms.locfileid: "39077961"
---
# <a name="ltcommandsgt-element-bootstrapper"></a>&lt;Komutları&gt; öğesi (Önyükleyici)
`Commands` Öğesi uygular öğelerce açıklanan testleri `InstallChecks` öğesi ve hangi paket bildirir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] önyükleyici, test başarısız olursa yüklemelisiniz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<Commands  
    Reboot  
>  
    <Command  
        PackageFile  
        Arguments  
        EstimatedInstallSeconds  
        EstimatedDiskBytes  
        EstimatedTempBytes  
        Log  
    >  
        <InstallConditions>  
            <BypassIf   
                Property  
                Compare  
                Value  
                Schedule  
            />  
            <FailIf   
                Property  
                Compare  
                Value  
                String  
                Schedule  
            />  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode   
                Value  
                Result  
                String  
            />  
        </ExitCodes>  
    </Command>  
</Commands>  
```  
  
## <a name="elements-and-attributes"></a>Öğeler ve öznitelikler  
 `Commands` Öğesi gereklidir. Öğe, aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Reboot`|İsteğe bağlı. Paketlerin herhangi bir yeniden başlatma çıkış kodu döndürmesi durumunda sistemin yeniden başlatılıp başlatılmayacağını belirler. Aşağıdaki liste, geçerli değerleri gösterir:<br /><br /> `Defer`. Yeniden başlatma, gelecekte süre kadar ertelenir.<br /><br /> `Immediate`. Hemen bir yeniden başlatma paketlerden birini bir yeniden başlatma çıkış kodu döndürdü neden olur.<br /><br /> `None`. Herhangi bir yeniden başlatma isteğinin yoksayılmasına neden olur.<br /><br /> Varsayılan, `Immediate` değeridir.|  
  
## <a name="command"></a>Komut  
 `Command` Öğesi alt öğesi olan `Commands` öğesi. A `Commands` öğesi bir veya daha fazla olabilir `Command` öğeleri. Öğe, aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`PackageFile`|Gerekli. Bir veya daha fazla tarafından belirtilen koşullar yüklemek için paket adını gereken `InstallConditions` false döndürün. Paket kullanarak aynı dosyayı tanımlanmalıdır bir `PackageFile` öğesi.|  
|`Arguments`|İsteğe bağlı. Paket dosyaya geçirilecek komut satırı bağımsız değişkenleri kümesi.|  
|`EstimatedInstallSeconds`|İsteğe bağlı. Paketi yüklemek için saniye cinsinden tahmini süre sürer. Bu değer kullanıcı için önyükleyici görüntülenir ilerleme çubuğu boyutunu belirler. 0, bu durumda tahmin belirtilen hiçbir zaman varsayılandır.|  
|`EstimatedDiskBytes`|İsteğe bağlı. Tahmini disk alanı, paket yükleme sonrasında kaplayacağı bayt miktarı tamamlandı. Bu değer kullanıcı için önyükleyici görüntülenir sabit disk alanı gereksinimleri kullanılır. Varsayılan, servis talebi önyükleyici herhangi bir sabit disk alanı gereksinimleri görüntülemez 0 ' dır.|  
|`EstimatedTempBytes`|İsteğe bağlı. Geçici disk alanı, paket gerektiren bayt cinsinden tahmini miktarı.|  
|`Log`|İsteğe bağlı. Paket, paketin kök dizinine göreli oluşturduğu günlük dosyası yolu.|  
  
## <a name="installconditions"></a>InstallConditions  
 `InstallConditions` Öğesi alt öğesi olan `Command` öğesi. Her `Command` öğesi, en fazla bir olabilir `InstallConditions` öğesi. Hayır ise `InstallConditions` öğesi yoksa, tarafından belirtilen paket `Condition` her zaman çalışır.  
  
## <a name="bypassif"></a>BypassIf  
 `BypassIf` Öğesi alt öğesi olan `InstallConditions` öğesi ve bir komut değil yürütülmelidir altında pozitif bir koşul açıklar. Her `InstallConditions` öğesi sıfır veya daha fazla olabilir `BypassIf` öğeleri.  
  
 `BypassIf` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sınanacak özellik adı. Özelliği daha önce bir alt öğesi tarafından tanımlanmış olmalıdır `InstallChecks` öğesi. Daha fazla bilgi için [ \<InstallChecks > öğesi](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Gerekli. Gerçekleştirilecek karşılaştırma türünü. Aşağıdaki liste, geçerli değerleri gösterir:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Gerekli. Özellikle Karşılaştırılacak değer.|  
|`Schedule`|İsteğe bağlı. Adı bir `Schedule` kuralın ne zaman değerlendirilmesi gerektiğini tanımlayan etiket.|  
  
## <a name="failif"></a>FailIf  
 `FailIf` Öğesi alt öğesi olan `InstallConditions` öğesi ve bir pozitif koşul altında yüklemenin durması açıklar. Her `InstallConditions` öğesi sıfır veya daha fazla olabilir `FailIf` öğeleri.  
  
 `FailIf` Aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Property`|Gerekli. Sınanacak özellik adı. Özelliği daha önce bir alt öğesi tarafından tanımlanmış olmalıdır `InstallChecks` öğesi. Daha fazla bilgi için [ \<InstallChecks > öğesi](../deployment/installchecks-element-bootstrapper.md).|  
|`Compare`|Gerekli. Gerçekleştirilecek karşılaştırma türünü. Aşağıdaki liste, geçerli değerleri gösterir:<br /><br /> `ValueEqualTo`, `ValueNotEqualTo`, `ValueGreaterThan`, `ValueGreaterThanOrEqualTo`, `ValueLessThan`, `ValueLessThanOrEqualTo`, `VersionEqualTo`, `VersionNotEqualTo`, `VersionGreaterThan`, `VersionGreaterThanOrEqualTo`, `VersionLessThan`, `VersionLessThanOrEqualTo`, `ValueExists`, `ValueNotExists`|  
|`Value`|Gerekli. Özellikle Karşılaştırılacak değer.|  
|`String`|İsteğe bağlı. Başarısızlık durumunda kullanıcıya görüntülenecek metin.|  
|`Schedule`|İsteğe bağlı. Adı bir `Schedule` kuralın ne zaman değerlendirilmesi gerektiğini tanımlayan etiket.|  
  
## <a name="exitcodes"></a>ExitCodes  
 `ExitCodes` Öğesi alt öğesi olan `Command` öğesi. `ExitCodes` Öğesi içeren bir veya daha fazla `ExitCode` paketinden yanıt çıkış kodu olarak ne yükleme yapması gerektiğini belirleyen öğeleri. Bir olabilir isteğe bağlı `ExitCode` öğesinin altında bir `Command` öğesi. `ExitCodes` öznitelikleri yok.  
  
## <a name="exitcode"></a>ExitCode  
 `ExitCode` Öğesi alt öğesi olan `ExitCodes` öğesi. `ExitCode` Paketinden yanıt çıkış kodu olarak ne yükleme yapması gerektiğini belirler. `ExitCode` alt öğe içerir ve aşağıdaki özniteliklere sahiptir.  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`Value`|Gerekli. Bu çıkış kodu değerini `ExitCode` öğesine uygular.|  
|`Result`|Gerekli. Yükleme için bu çıkış kodu nasıl tepki. Aşağıdaki liste, geçerli değerleri gösterir:<br /><br /> `Success`. Paket başarıyla yüklendi olarak işaretler.<br /><br /> `SuccessReboot`. Paketi başarıyla yüklendi olarak işaretler ve sistemin yeniden yönlendirir.<br /><br /> `Fail`. Paket başarısız olarak işaretler.<br /><br /> `FailReboot`. Paket başarısız olarak işaretler ve sistemin yeniden yönlendirir.|  
|`String`|İsteğe bağlı. Bu çıkış kodu yanıt kullanıcıya görüntülenecek değer.|  
|`FormatMessageFromSystem`|İsteğe bağlı. Çıkış koduna karşılık gelen sistem tarafından sağlanan hata iletisini kullanabilir veya sağlanan değeri belirler `String`. Geçerli değerler `true`, yani sistem tarafından sağlanan hata kullanmak ve `false`, yani tarafından sağlanan dizenin kullanılacak `String`. Varsayılan, `false` değeridir. Bu özellik ise `false`, ancak `String` ayarlanmazsa sistem tarafından sağlanan hata kullanılacaktır.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, .NET Framework 2.0 yükleme komutları tanımlar.  
  
```xml  
<Commands Reboot="Immediate">  
    <Command PackageFile="instmsia.exe"  
             Arguments= ' /q /c:"msiinst /delayrebootq"'  
             EstimatedInstallSeconds="20" >  
        <InstallConditions>  
           <BypassIf Property="VersionNT" Compare="ValueExists"/>  
             BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="2.0"/>  
        </InstallConditions>  
        <ExitCodes>  
            <ExitCode Value="0" Result="SuccessReboot"/>  
            <ExitCode Value="1641" Result="SuccessReboot"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
    </Command>  
    <Command PackageFile="WindowsInstaller-KB884016-v2-x86.exe"  
             Arguments= '/quiet /norestart'   
             EstimatedInstallSeconds="20" >  
      <InstallConditions>  
          <BypassIf Property="Version9x" Compare="ValueExists"/>  
          <BypassIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3"/>  
          <BypassIf Property="VersionMsi" Compare="VersionGreaterThanOrEqualTo" Value="3.0"/>  
          <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
      </InstallConditions>  
      <ExitCodes>  
          <ExitCode Value="0" Result="Success"/>  
          <ExitCode Value="1641" Result="SuccessReboot"/>  
          <ExitCode Value="3010" Result="SuccessReboot"/>  
          <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
      </ExitCodes>  
    </Command>  
    <Command PackageFile="dotnetfx.exe"   
         Arguments=' /q:a /c:"install /q /l"'   
         EstimatedInstalledBytes="21000000"   
         EstimatedInstallSeconds="300">  
  
        <!-- These checks determine whether the package is to be installed -->  
        <InstallConditions>  
            <!-- Either of these properties indicates the .NET Framework is already installed -->  
            <BypassIf Property="DotNetInstalled" Compare="ValueNotEqualTo" Value="0"/>  
  
            <!-- Block install if user does not have adminpermissions -->  
            <FailIf Property="AdminUser" Compare="ValueEqualTo" Value="false" String="AdminRequired"/>  
  
            <!-- Block install on Windows 95 -->  
            <FailIf Property="Version9X" Compare="VersionLessThan" Value="4.10" String="InvalidPlatformWin9x"/>  
  
            <!-- Block install on Windows 2000 SP 2 or less -->  
            <FailIf Property="VersionNT" Compare="VersionLessThan" Value="5.0.3" String="InvalidPlatformWinNT"/>  
  
            <!-- Block install if Internet Explorer 5.01 or later is not present -->  
            <FailIf Property="IEVersion" Compare="ValueNotExists" String="InvalidPlatformIE" />  
            <FailIf Property="IEVersion" Compare="VersionLessThan" Value="5.01" String="InvalidPlatformIE" />  
  
            <!-- Block install if the operating system does not support x86 -->  
            <FailIf Property="ProcessorArchitecture" Compare="ValueNotEqualTo" Value="Intel" String="InvalidPlatformArchitecture" />  
       </InstallConditions>  
  
        <ExitCodes>  
            <ExitCode Value="0" Result="Success"/>  
            <ExitCode Value="3010" Result="SuccessReboot"/>  
            <ExitCode Value="4097" Result="Fail" String="AdminRequired"/>  
            <ExitCode Value="4098" Result="Fail" String="WindowsInstallerComponentFailure"/>  
            <ExitCode Value="4099" Result="Fail" String="WindowsInstallerImproperInstall"/>  
            <ExitCode Value="4101" Result="Fail" String="AnotherInstanceRunning"/>  
            <ExitCode Value="4102" Result="Fail" String="OpenDatabaseFailure"/>  
            <ExitCode Value="4113" Result="Fail" String="BetaNDPFailure"/>  
            <DefaultExitCode Result="Fail" FormatMessageFromSystem="true" String="GeneralFailure" />  
        </ExitCodes>  
  
    </Command>  
</Commands>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ürün ve paket şema başvurusu](../deployment/product-and-package-schema-reference.md)   
 [\<InstallChecks > öğesi](../deployment/installchecks-element-bootstrapper.md)