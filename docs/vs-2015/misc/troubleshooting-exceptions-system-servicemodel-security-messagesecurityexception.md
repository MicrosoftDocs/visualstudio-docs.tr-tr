---
title: 'Özel durum sorunlarını giderme: System.ServiceModel.Security.MessageSecurityException | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e7d13f5cc282026b1590f59180ed7f25312bb926
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742473"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Özel Durum Sorunlarını Giderme: System.ServiceModel.Security.MessageSecurityException
A <xref:System.ServiceModel.Security.MessageSecurityException> özel durum [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] bir ileti doğru güvenli olmayan veya oynanmış belirler. Hata, en sık aşağıdaki koşulların tümü doğru olduğunda oluşur:  
  
-   (.Svc) bir Web sitesi veya Web uygulama projesinde bir WCF Hizmeti ile iletişim kurmak için bir WCF hizmet başvurusu Uzak Masaüstü bağlantısı veya Terminal Services gibi uzak bir bağlantısı kullanın.  
  
-   Uzak site üzerinde yönetici izinlerine sahip değil.  
  
-   Uzak sitede localhost isteklerine tarafından işlendiğinden [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] geliştirme sunucusu.  
  
## <a name="associated-tips"></a>İlişkili ipuçları  
 **ASP.Net geliştirme sunucusu kullanırken, NTLM kimlik doğrulama sorunları çözün.**  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Geliştirme sunucusu, genellikle anonim erişime izin veren kapalı, Windows NT Sınama/Yanıt (NTLM) güvenlik vardır. Terminal Hizmetleri oturumunda çalıştırın veya bir uzak bağlantı kullandığınızda varsayılan olarak, NTLM güvenlik etkin. NTLM etkinleştirildiğinde, tüm localhost istekleri karşı başlatılan işlem ya da kullanıcı kimlik bilgileri doğrulandıktan [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] geliştirme sunucusu. Bu, güvenlik tehditlerini azaltır. Ancak, WCF Ayrıca kendi kimlik doğrulaması gerçekleştirir ve WCF hizmetlerini yönetici olmayan hesaba izin vermez.  
  
 Kullanarak bir uzak kullanıcının Web sitesi çalışabilir, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] geliştirme Sunucusu'nda ve ayrıca bir Web hizmeti veya WCF Hizmeti ile çalışma, bir özel hizmet bağlaması oluşturun veya NTLM güvenliği devre dışı.  
  
> [!IMPORTANT]
>  NTLM güvenliğin devre dışı bırakılması önerilmez ve bir güvenlik tehdidi yol açabilir.  
  
 Özel hizmet bağlaması oluşturursanız, yine de NTLM kimlik doğrulaması tarafından korunur.  
  
 WCF hizmeti için özel hizmet bağlaması oluşturmak için aşağıdaki adımları kullanın.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Bağlama içinde ASP.NET Development Server'da barındırılan WCF hizmeti için özel bir hizmet oluşturmak için  
  
1. Özel durum oluşturan WCF hizmeti için Web.config dosyasını açın.  
  
2. Web.config dosyasına aşağıdaki bilgileri girin.  
  
   ```  
   <bindings>  
     <customBinding>  
       <binding name="Service1Binding">  
         <transactionFlow />  
         <textMessageEncoding />  
         <httpTransport authenticationScheme="Ntlm" />  
       </binding>  
     </customBinding>  
   </bindings>  
   ```  
  
3. Web.config dosyasını kaydedip kapatın.  
  
4. WCF veya Web hizmeti kodunda bir uç nokta değeri şu şekilde değiştirin:  
  
   ```  
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
   ```  
  
    Bu, hizmetin özel bağlama kullanmasını sağlar.  
  
5. Hizmete erişen bir Web uygulamasında bir hizmet başvurusu ekleyin. (İçinde **hizmet Başvurusu Ekle** iletişim kutusunda, özel durum oluşturan özgün hizmetiyle yaptığınız gibi hizmetin bir başvuru ekleyin.)  
  
   Bir WCF hizmet başvurusu ile çalışırken, NTLM güvenliğini devre dışı bırakmak için aşağıdaki adımları izleyebilirsiniz.  
  
> [!IMPORTANT]
>  NTLM güvenliğin devre dışı bırakılması önerilmez ve bir güvenlik tehdidi yol açabilir.  
  
#### <a name="to-turn-off-ntlm-security"></a>NTLM güvenliğini devre dışı kapatmak için  
  
1.  İçinde **Çözüm Gezgini**Web sitesi adına sağ tıklayın ve ardından **özellik sayfaları**.  
  
2.  Seçin **Başlat seçenekleri**ve ardından temizlemek **NTLM kimlik doğrulaması** onay kutusu.  
  
3.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Özel durum Yardımcısını kullanma](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)