---
title: 'Nasıl yapılır: araç için Web.Config dosyalarını değiştirme ve dinamik olarak derlenmiş ASP.NET Web uygulamalarının profilini | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f668bebb2967ca89feb1c6f52f00253ac3eb07b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807757"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Nasıl yapılır: Dinamik Olarak Derlenmiş ASP.NET Web Uygulamalarını İzlemek ve Profilini Oluşturmak için Web.Config Dosyalarını Değiştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanabileceğiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] dinamik olarak ayrıntılı zamanlama verileri, .NET bellek ayırma verilerinin ve .NET nesne ömür verilerini toplamak için profil oluşturma araçları izleme metodunu derlenmiş [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları.  
  
 Bu konu, izlemeyi ve profillerinin oluşturulmasını etkinleştirmek için web.config yapılandırma dosyası değiştirilecek açıklar [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları.  
  
> [!NOTE]
>  Örnekleme profili oluşturma yöntemi kullandığınızda veya önceden derlenmiş bir araç haline getirmek istediğinizde web.config dosyasını değiştirmeniz gerekmez [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] modülü.  
  
 Kök web.config dosyasının **yapılandırma** öğesi. İzleme ve dinamik olarak derlenmiş bir profil için [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulaması, aşağıdaki öğeleri eklediğinizde veya gerekir:  
  
- A **yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly** profil oluşturma denetleyen Microsoft.VisualStudio.Enterprise.ASPNetHelper derleme tanımlayan öğesi. **DependentAssembly** öğesi iki alt öğeleri içerir: **assemblyIdentity** ve **codeBase**.  
  
- A **configuration/system.web/compilation** hedef bütünleştirilmiş kod profil oluşturucu işlem sonrası bir derleme adımı tanımlayan öğesi.  
  
- İki **ekleme** profil oluşturma Araçlar konumunu tanımlayan öğeleri eklenir **configuration/appSettings** bölümü.  
  
  Uygulama yapılandırmasını geri yüklemek için kullanabileceğiniz özgün web.config dosyasının bir kopyasını oluşturmanızı öneririz.  
  
### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly öğesi olarak ASPNetHelper derleme eklemek için  
  
1.  Gerekirse, ekleme **çalışma zamanı** öğesi alt öğesi olarak **yapılandırma** öğesi; Aksi halde, sonraki adıma geçin.  
  
     **Çalışma zamanı** öğesi özniteliklere sahip değildir. **Yapılandırma** öğesi yalnızca bir olabilir **çalışma zamanı** alt öğesi.  
  
2.  Gerekirse, ekleme **assemblyBinding** öğesi alt öğesi olarak **çalışma zamanı** öğesi; Aksi halde, sonraki adıma geçin.  
  
     **Çalışma zamanı** öğesi yalnızca bir olabilir **assemblyBinding** öğesi.  
  
3.  Aşağıdaki öznitelik adı ekleyin ve değerini **assemblyBinding** öğesi:  
  
    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**xmlns**|**urn: schemas-microsoft-com:asm.v1**|  
  
4.  Ekleme bir **dependentAssembly** öğesi alt öğesi olarak **assemblyBinding** öğesi.  
  
     **DependentAssembly** öğesi özniteliklere sahip değildir.  
  
5.  Ekleme bir **assemblyIdentity** öğesi alt öğesi olarak **dependentAssembly** öğesi.  
  
6.  Aşağıdaki öznitelik adları ve değerleri eklemek **assemblyIdentity** öğesi:  
  
    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**Adı**|**Microsoft.VisualStudio.Enterprise.ASPNetHelper**|  
    |**PublicKeyToken**|**b03f5f7f11d50a3a**|  
    |**Kültür**|**Nötr**|  
  
7.  Ekleme bir **codeBase** öğesi alt öğesi olarak **dependentAssembly** öğesi.  
  
8.  Aşağıdaki öznitelik adları ve değerleri eklemek **codeBase** öğesi:  
  
    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**version**|**10.0.0.0**|  
    |**href**|`PathToASPNetHelperDll`|  
  
     `PathToASPNetHelperDll` Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll dosyası URL'sidir. Varsa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] varsayılan konumunda yüklü **href** değeri olmalıdır. `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  
  
```  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity                         name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"                         culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
```  
  
### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Profiler işlem sonrası adımı configuration/system.web/compilation öğesine eklemek için  
  
1.  Gerekirse, ekleme **system.web** öğesi alt öğesi olarak **yapılandırma** öğesi; Aksi halde, sonraki adıma geçin.  
  
     **System.web** öğesi özniteliklere sahip değildir. **Yapılandırma** öğesi yalnızca bir olabilir **system.web** alt öğesi.  
  
2.  Gerekirse, ekleme **derleme** öğesi alt öğesi olarak **system.web** öğesi; Aksi halde, sonraki adıma geçin.  
  
     **System.web** öğesi yalnızca bir olabilir **derleme** alt öğesi.  
  
3.  Mevcut herhangi özniteliklerden kaldırın **derleme** öğesini ve aşağıdaki öznitelik adı ve değeri ekleyin:  
  
    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, sürüm 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
    <configuration>  
```  
  
### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Profiler konumu ayarları configuration/appSettings öğesine eklemek için  
  
1.  Gerekirse, ekleme **appSettings** öğesi alt öğesi olarak **yapılandırma** öğesi; Aksi halde, sonraki adıma geçin.  
  
     **AppSettings** öğesi özniteliklere sahip değildir. **Yapılandırma** öğesi yalnızca bir olabilir **appSettings** alt öğesi.  
  
2.  Ekleme bir **ekleme** öğesi alt öğesi olarak **appSettings** öğesi.  
  
3.  Aşağıdaki öznitelik adları ve değerleri eklemek **ekleme** öğesi:  
  
    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**Anahtarı**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation**|  
    |**value**|`PerformanceToolsFolder` **\VSInstr.exe**|  
  
4.  Başka bir **ekleme** öğesi alt öğesi olarak **appSettings** öğesi.  
  
5.  Aşağıdaki öznitelik adları ve değerleri için bu ekleme **ekleme** öğesi:  
  
    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**Anahtarı**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
    |**value**|`PerformanceToolsFolder`|  
  
     `PerformanceToolsFolder` Profil Oluşturucu yürütülebilir dosyalar yoludur. Varsa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] yüklü varsayılan konumunda değer olacaktır **C:\Program Files\Microsoft Visual Studio 10.0\Team Araçlar\Performans araçları**  
  
```  
    <configuration>  
        <runtime>  
        . . .  
        </runtime>  
        . . .  
        <system.web>  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
        />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
```  
  
## <a name="example"></a>Örnek  
 Aşağıdaki izleme ve profillerinin oluşturulmasını sağlayan bir tam web.config dosyasıdır dinamik olarak derlenmiş [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Web uygulamaları. Bu örnek, diğer hiçbir ayarlarında değişiklik önce bir dosya olduğunu varsayar.  
  
```  
<?xml version="1.0"?>  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity   
                        name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
                        publicKeyToken="b03f5f7f11d50a3a"  
                        culture="neutral"   
                    />  
                    <codeBase   
                        version="10.0.0.0"  
                        href="file:///C:/Program%20Files/Microsoft%20Visual%20Studio%2010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL"   
                    />  
                </dependentAssembly>  
            </assemblyBinding>  
        </runtime>  
        <system.web>  
            <compilation  
                assemblyPostProcessorType="Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter,  
                    Microsoft.VisualStudio.Enterprise.ASPNetHelper,  
                    Version=10.0.0.0,  
                    Culture=neutral,  
                    PublicKeyToken=b03f5f7f11d50a3a"   
            />  
        </system.web>  
        <appSettings>  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\vsinstr.exe"  
            />  
            <add  
                key="Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools"  
                value="C:\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools\"  
            />  
        </appSettings>  
    </configuration>  
  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET Uygulamasın izleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-detailed-timing-data-with-the-profiler-by-using-the-command-line.md)   
 [Nasıl Yapılır: Dinamik Olarak Derlenmiş Bir ASP.NET Uygulamasını İzleme ve Bellek Verileri Toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data-by-using-the-profiler-command-line.md)



