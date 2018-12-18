---
title: 'Nasıl yapılır: araç için Web.Config dosyalarını değiştirme ve dinamik olarak derlenmiş ASP.NET Web uygulamalarının profilini | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a92e5692-2183-4ae3-9431-b067c6a7aab4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- aspnet
ms.openlocfilehash: 521da3263d3ea893613bf3b5211763230d07c67f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830996"
---
# <a name="how-to-modify-webconfig-files-to-instrument-and-profile-dynamically-compiled-aspnet-web-applications"></a>Nasıl yapılır: izleme ve profil dinamik olarak derlenmiş ASP.NET web uygulamaları için web.config dosyalarını değiştirme
Kullanabileceğiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dinamik olarak ayrıntılı zamanlama verileri, .NET bellek ayırma verilerinin ve .NET nesne ömür verilerini toplamak için profil oluşturma araçları izleme metodunu derlenmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları.  

 Bu konu nasıl değiştirileceğini açıklar *web.config* araçları ve profillerinin oluşturulmasını etkinleştirmek için yapılandırma dosyası [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları.  

> [!NOTE]
>  Değişiklik gerekmez *web.config* dosya örnekleme profili oluşturma yöntemi kullanırken ya da önceden derlenmiş bir araç haline getirmek istediğinizde [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] modülü.  

 Kök bir *web.config* dosyasıdır **yapılandırma** öğesi. İzleme ve dinamik olarak derlenmiş bir profil için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] web uygulaması, aşağıdaki öğeleri eklediğinizde veya gerekir:  

- A **yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly** profil oluşturma denetleyen Microsoft.VisualStudio.Enterprise.ASPNetHelper derleme tanımlayan öğesi. **DependentAssembly** öğesi iki alt öğeleri içerir: **assemblyIdentity** ve **codeBase**.  

- A **configuration/system.web/compilation** hedef bütünleştirilmiş kod profil oluşturucu işlem sonrası bir derleme adımı tanımlayan öğesi.  

- İki **ekleme** profil oluşturma Araçlar konumunu tanımlayan öğeleri eklenir **configuration/appSettings** bölümü.  

  Özgün bir kopyasını oluşturmanızı öneririz *web.config* uygulama yapılandırmasını geri yüklemek için kullanabileceğiniz dosyası.  

### <a name="to-add-the-aspnethelper-assembly-as-a-configurationruntimeassemblybindingdependentassembly-element"></a>Yapılandırma/çalışma zamanı/assemblyBinding/dependentAssembly öğesi olarak ASPNetHelper derleme eklemek için  

1. Gerekirse, ekleme **çalışma zamanı** öğesi alt öğesi olarak **yapılandırma** öğesi; Aksi halde, sonraki adıma geçin.  

    **Çalışma zamanı** öğesi özniteliklere sahip değildir. **Yapılandırma** öğesi yalnızca bir olabilir **çalışma zamanı** alt öğesi.  

2. Gerekirse, ekleme **assemblyBinding** öğesi alt öğesi olarak **çalışma zamanı** öğesi; Aksi halde, sonraki adıma geçin.  

    **Çalışma zamanı** öğesi yalnızca bir olabilir **assemblyBinding** öğesi.  

3. Aşağıdaki öznitelik adı ekleyin ve değerini **assemblyBinding** öğesi:  


   | Öznitelik adı | Öznitelik değeri |
   |----------------|--------------------------------------|
   | **xmlns** | **urn: schemas-microsoft-com:asm.v1** |


4. Ekleme bir **dependentAssembly** öğesi alt öğesi olarak **assemblyBinding** öğesi.  

    **DependentAssembly** öğesi özniteliklere sahip değildir.  

5. Ekleme bir **assemblyIdentity** öğesi alt öğesi olarak **dependentAssembly** öğesi.  

6. Aşağıdaki öznitelik adları ve değerleri eklemek **assemblyIdentity** öğesi:  


   | Öznitelik adı | Öznitelik değeri |
   |--------------------| - |
   | **Adı** | **Microsoft.VisualStudio.Enterprise.ASPNetHelper** |
   | **PublicKeyToken** | **b03f5f7f11d50a3a** |
   | **Kültür** | **Nötr** |


7. Ekleme bir **codeBase** öğesi alt öğesi olarak **dependentAssembly** öğesi.  

8. Aşağıdaki öznitelik adları ve değerleri eklemek **codeBase** öğesi:  

   |Öznitelik adı|Öznitelik değeri|  
   |--------------------|---------------------|  
   |**version**|**10.0.0.0**|  
   |**href**|`PathToASPNetHelperDll`|  

    `PathToASPNetHelperDll` Microsoft.VisualStudio.Enterprise.ASPNetHelper.dll dosyası URL'sidir. Varsa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varsayılan konumunda yüklü **href** değeri olmalıdır. `C:/Program%20Files/Microsoft%20Visual%20Studio%202010.0/Common7/IDE/PrivateAssemblies/Microsoft.VisualStudio.Enterprise.ASPNetHelper.DLL`  

```xml  
    <configuration>  
        <runtime>  
            <assemblyBinding   
                xmlns="urn:schemas-microsoft-com:asm.v1"  
            >  
                <dependentAssembly>  
                    <assemblyIdentity name="Microsoft.VisualStudio.Enterprise.ASPNetHelper"   
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
```  

### <a name="to-add-the-profiler-post-process-step-to-the-configurationsystemwebcompilation-element"></a>Profil Oluşturucu işlem sonrası adımı configuration/system.web/compilation öğesine eklemek için  

1.  Gerekirse, ekleme **system.web** öğesi alt öğesi olarak **yapılandırma** öğesi; Aksi halde, sonraki adıma geçin.  

     **System.web** öğesi özniteliklere sahip değildir. **Yapılandırma** öğesi yalnızca bir olabilir **system.web** alt öğesi.  

2.  Gerekirse, ekleme **derleme** öğesi alt öğesi olarak **system.web** öğesi; Aksi halde, sonraki adıma geçin.  

     **System.web** öğesi yalnızca bir olabilir **derleme** alt öğesi.  

3.  Mevcut herhangi özniteliklerden kaldırın **derleme** öğesini ve aşağıdaki öznitelik adı ve değeri ekleyin:  

    |Öznitelik adı|Öznitelik değeri|  
    |--------------------|---------------------|  
    |**assemblyPostProcessorType**|**Microsoft.VisualStudio.Enterprise.Common.AspPerformanceInstrumenter, Microsoft.VisualStudio.Enterprise.ASPNetHelper, sürüm 10.0.0.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a**|  

```xml  
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

### <a name="to-add-profiler-location-settings-to-the-configurationappsettings-element"></a>Profil Oluşturucu konumu ayarları configuration/appSettings öğesine eklemek için  

1. Gerekirse, ekleme **appSettings** öğesi alt öğesi olarak **yapılandırma** öğesi; Aksi halde, sonraki adıma geçin.  

    **AppSettings** öğesi özniteliklere sahip değildir. **Yapılandırma** öğesi yalnızca bir olabilir **appSettings** alt öğesi.  

2. Ekleme bir **ekleme** öğesi alt öğesi olarak **appSettings** öğesi.  

3. Aşağıdaki öznitelik adları ve değerleri eklemek **ekleme** öğesi:  


   | Öznitelik adı | Öznitelik değeri |
   |----------------| - |
   | **Anahtarı** | **Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrLocation** |
   | **value** | `PerformanceToolsFolder` **\VSInstr.exe** |


4. Başka bir **ekleme** öğesi alt öğesi olarak **appSettings** öğesi.  

5. Aşağıdaki öznitelik adları ve değerleri için bu ekleme **ekleme** öğesi:  

   |Öznitelik adı|Öznitelik değeri|  
   |--------------------|---------------------|  
   |**Anahtarı**|**Microsoft.VisualStudio.Enterprise.AspNetHelper.VsInstrTools**|  
   |**value**|`PerformanceToolsFolder`|  

    `PerformanceToolsFolder` Profil Oluşturucu yürütülebilir dosyalar yoludur. Varsa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yüklü varsayılan konumunda değer olacaktır **C:\Program Files\Microsoft Visual Studio 10.0\Team Araçlar\Performans araçları**  

```xml  
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
 Aşağıdaki bir tamamlandıktan *web.config* araçları ve profillerinin dinamik olarak oluşturulmasını sağlayan dosya derlenmiş [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamaları. Bu örnek, diğer hiçbir ayarlarında değişiklik önce bir dosya olduğunu varsayar.  

```xml  
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

## <a name="see-also"></a>Ayrıca bkz.  
 [Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET uygulamasını izleme ve ayrıntılı zamanlama verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-app-and-collect-timing-data.md)   
 [Nasıl yapılır: dinamik olarak derlenmiş bir ASP.NET uygulamasını izleme ve bellek verileri toplama](../profiling/how-to-instrument-a-dynamically-compiled-aspnet-web-application-and-collect-memory-data.md)