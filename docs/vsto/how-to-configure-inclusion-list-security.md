---
title: 'Nasıl yapılır: ekleme listesi güvenliğini yapılandırma'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- permissions [Office development in Visual Studio
- inclusion lists [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6e5bd1794b76485d60588b94d3ca139a314f9723
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255843"
---
# <a name="how-to-configure-inclusion-list-security"></a>Nasıl yapılır: ekleme listesi güvenliğini yapılandırma
  Yönetici izinlerine sahipseniz, yapılandırabileceğiniz [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] denetlemek için son kullanıcıların Office çözümleri listesine bir güven kararı kaydederek yükleme seçeneği verilip verilmediğini güven istemi. Ekleme listeleri hakkında daha fazla bilgi için bkz: [ekleme listeleri kullanarak güven Office çözümleri](../vsto/trusting-office-solutions-by-using-inclusion-lists.md).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Her beş bölgeleri çözümleri için aşağıdaki seçenekleri ayarlayabilirsiniz:  
  
-   Etkinleştirme [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi anahtarını ve ekleme listesi. Son kullanıcıların herhangi bir sertifika ile imzalanmış Office çözümlerine güven verme izin verebilirsiniz.  
  
-   Kısıtlama [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi anahtarını ve ekleme listesi. Yayımcı tanımlar, ancak zaten güvenilir olmayan bir sertifikayla imzalanmış Office çözümleri yüklemek son kullanıcılara izin verebilirsiniz.  
  
-   Devre dışı [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] güven istemi anahtarını ve ekleme listesi. Son kullanıcılar açıkça güvenilir bir sertifika ile imzalanmamış herhangi bir Office çözümü yüklemesini engelleyebilir.  
  
## <a name="enable-the-inclusion-list"></a>Ekleme listesini etkinleştir  
 Son kullanıcılara bu bölgeden gelen herhangi bir Office çözümü çalıştırma ve yükleme seçeneğiyle gösterilmesini istediğiniz zaman bir bölgenin ekleme listesi etkinleştirin.  
  
### <a name="to-enable-the-inclusion-list-by-using-the-registry-editor"></a>Kayıt Defteri Düzenleyicisi'ni kullanarak ekleme listesini etkinleştirmek için  
  
1.  Kayıt Defteri Düzenleyicisi'ni açın:  
  
    1.  Tıklatın **Başlat**ve ardından **çalıştırmak**.  
  
    2.  İçinde **açık** kutusuna **regedt32.exe**ve ardından **Tamam**.  
  
2.  Aşağıdaki kayıt defteri anahtarını bulun:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Anahtar mevcut değilse oluşturun.  
  
3.  Aşağıdaki alt anahtarları olarak ekleyin **dize değeri**, zaten ilişkili değerleri ile birlikte mevcut değil.  
  
    |Dize değeri alt anahtarı|Değer|  
    |-------------------------|-----------|  
    |**Internet**|**AuthenticodeRequired**|  
    |**UntrustedSites**|**devre dışı**|  
    |**Bilgisayarım**|**Etkin**|  
    |**LocalIntranet**|**Etkin**|  
    |**TrustedSites**|**Etkin**|  
  
     Varsayılan olarak, **Internet** değerine sahip **AuthenticodeRequired** ve **UntrustedSites** değerine sahip **devre dışı**.  
  
### <a name="to-enable-the-inclusion-list-programmatically"></a>Ekleme listesini programlı olarak etkinleştirmek için  
  
1.  Visual Basic veya Visual C# konsol uygulaması oluşturun.  
  
2.  Açık *Program.vb* veya *Program.cs* dosya düzenleme için ve aşağıdaki kodu ekleyin.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Enabled")  
    key.SetValue("LocalIntranet", "Enabled")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "Enabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Enabled");  
    key.SetValue("LocalIntranet", "Enabled");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "Enabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Derleme ve uygulamayı çalıştırın.  
  
## <a name="restrict-the-inclusion-list"></a>Ekleme listesini kısıtlamak  
 Çözümleri, kullanıcılar için bir güven kararı istenir önce kimlik bilmesinin Authenticode sertifikaları kullanılarak imzalanmalıdır. böylece ekleme listesini sınırlayın.  
  
### <a name="to-restrict-the-inclusion-list"></a>Ekleme listesini kısıtlamak için  
  
1.  Kayıt Defteri Düzenleyicisi'ni açın:  
  
    1.  Tıklatın **Başlat**ve ardından **çalıştırmak**.  
  
    2.  İçinde **açık** kutusuna **regedt32.exe**ve ardından **Tamam**.  
  
2.  Aşağıdaki kayıt defteri anahtarını bulun:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
     Anahtar mevcut değilse oluşturun.  
  
3.  Aşağıdaki alt anahtarları olarak ekleyin **dize değeri**, zaten ilişkili değerleri ile birlikte mevcut değil.  
  
    |Dize değeri alt anahtarı|Değer|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**devre dışı**|  
    |**Internet**|**AuthenticodeRequired**|  
    |**Bilgisayarım**|**AuthenticodeRequired**|  
    |**LocalIntranet**|**AuthenticodeRequired**|  
    |**TrustedSites**|**AuthenticodeRequired**|  
  
     Varsayılan olarak, **Internet** değerine sahip **AuthenticodeRequired** ve **UntrustedSites** değerine sahip **devre dışı**.  
  
### <a name="to-restrict-the-inclusion-list-programmatically"></a>Ekleme listesini programlı olarak kısıtlamak için  
  
1.  Visual Basic veya Visual C# konsol uygulaması oluşturun.  
  
2.  Açık *Program.vb* veya *Program.cs* dosya düzenleme için ve aşağıdaki kodu ekleyin.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "AuthenticodeRequired")  
    key.SetValue("LocalIntranet", "AuthenticodeRequired")  
    key.SetValue("Internet", "AuthenticodeRequired")  
    key.SetValue("TrustedSites", "AuthenticodeRequired")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "AuthenticodeRequired");  
    key.SetValue("LocalIntranet", "AuthenticodeRequired");  
    key.SetValue("Internet", "AuthenticodeRequired");  
    key.SetValue("TrustedSites", "AuthenticodeRequired");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
    ```  
  
3.  Derleme ve uygulamayı çalıştırın.  
  
## <a name="disable-the-inclusion-list"></a>Ekleme listesi devre dışı bırak  
 Son kullanıcılar yalnızca güvenilir ve bilinen bir sertifikayla imzalanmış çözümleri yükleyebilmek ekleme listesi devre dışı bırakabilirsiniz.  
  
### <a name="to-disable-the-inclusion-list"></a>Ekleme listesi devre dışı bırakmak için  
  
1.  Kayıt Defteri Düzenleyicisi'ni açın:  
  
    1.  Tıklatın **Başlat**ve ardından **çalıştırmak**.  
  
    2.  İçinde **açık** kutusuna **regedt32.exe**ve ardından **Tamam**.  
  
2.  Bu zaten yoksa, aşağıdaki kayıt defteri anahtarı oluşturun:  
  
     **\HKEY_LOCAL_MACHINE\SOFTWARE\MICROSOFT\\. NETFramework\Security\TrustManager\PromptingLevel**  
  
3.  Aşağıdaki alt anahtarları olarak ekleyin **dize değeri**, zaten ilişkili değerleri ile birlikte mevcut değil.  
  
    |Dize değeri alt anahtarı|Değer|  
    |-------------------------|-----------|  
    |**UntrustedSites**|**devre dışı**|  
    |**Internet**|**devre dışı**|  
    |**Bilgisayarım**|**devre dışı**|  
    |**LocalIntranet**|**devre dışı**|  
    |**TrustedSites**|**devre dışı**|  
  
### <a name="to-disable-the-inclusion-list-programmatically"></a>Ekleme listesi program aracılığıyla devre dışı bırakmak için  
  
1.  Visual Basic veya Visual C# konsol uygulaması oluşturun.  
  
2.  Açık *Program.vb* veya *Program.cs* dosya düzenleme için ve aşağıdaki kodu ekleyin.  
  
    ```vb  
    Dim key As Microsoft.Win32.RegistryKey  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\MICROSOFT\.NETFramework\Security\TrustManager\PromptingLevel")  
    key.SetValue("MyComputer", "Disabled")  
    key.SetValue("LocalIntranet", "Disabled")  
    key.SetValue("Internet", "Disabled")  
    key.SetValue("TrustedSites", "Disabled")  
    key.SetValue("UntrustedSites", "Disabled")  
    key.Close()  
    ```  
  
    ```csharp  
    Microsoft.Win32.RegistryKey key;  
    key = Microsoft.Win32.Registry.LocalMachine.CreateSubKey("SOFTWARE\\MICROSOFT\\.NETFramework\\Security\\TrustManager\\PromptingLevel");  
    key.SetValue("MyComputer", "Disabled");  
    key.SetValue("LocalIntranet", "Disabled");  
    key.SetValue("Internet", "Disabled");  
    key.SetValue("TrustedSites", "Disabled");  
    key.SetValue("UntrustedSites", "Disabled");  
    key.Close();  
  
    ```  
  
3.  Derleme ve uygulamayı çalıştırın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Ekleme listelerini kullanarak Office çözümlerine güven](../vsto/trusting-office-solutions-by-using-inclusion-lists.md)   
 [Office çözümleri güvenli](../vsto/securing-office-solutions.md)  
  
  