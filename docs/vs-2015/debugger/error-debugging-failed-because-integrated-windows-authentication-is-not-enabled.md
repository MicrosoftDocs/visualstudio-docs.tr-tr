---
title: 'Hata: Tümleşik Windows kimlik doğrulaması etkinleştirilmediğinden hata ayıklama başarısız oldu | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_ntlm_authn_not_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6027cd94-74cf-470f-b7ce-6f6b68bc56ba
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0b922e8e8fde8b185207810d107afb9a9c5a6e05
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51757253"
---
# <a name="error-debugging-failed-because-integrated-windows-authentication-is-not-enabled"></a>Hata: Tümleşik Windows Kimlik Doğrulaması Etkinleştirilmediğinden Hata Ayıklama Başarısız
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklama isteyen kullanıcının kimlik doğrulaması, kimlik doğrulama hatası tarafından engellendi. Bir Web uygulaması veya bir XML Web hizmeti adımlamak çalıştığınızda ortaya çıkabilir. Bu hatanın bir nedeni, tümleşik Windows kimlik doğrulamasının etkin olduğunu. Bunu etkinleştirmek için "Tümleşik Windows kimlik doğrulamasını etkinleştirmek için." bulunan adımları izleyin.  
  
 Tümleşik Windows kimlik doğrulaması etkin ve bu hatayı görünmeye devam eder, çünkü bu hataya neden olduğunu mümkün **Windows etki alanı sunucuları için Özet kimlik doğrulaması** etkinleştirilir. Bu durumda, ağ yöneticinize başvurmanız gerekir.  
  
### <a name="to-enable-integrated-windows-authentication"></a>Tümleşik Windows kimlik doğrulamasını etkinleştirmek için  
  
1.  Web sunucusunda bir yönetici hesabını kullanarak oturum açın.  
  
2.  Tıklayın **Başlat** ve ardından **Denetim Masası**.  
  
3.  İçinde **Denetim Masası**, çift **Yönetimsel Araçlar**.  
  
4.  Çift **Internet Information Services**.  
  
5.  Web sunucusu düğümüne tıklayın.  
  
     A **Web siteleri** klasörü altında sunucu adına açar.  
  
6.  Kimlik doğrulaması için tüm Web sitelerinin veya tek tek Web siteleri için yapılandırabilirsiniz. Tüm Web siteleri için kimlik doğrulaması yapılandırmak için sağ **Web siteleri** klasörünü ve ardından **özellikleri**. Tek bir Web sitesi kimlik doğrulamasını yapılandırmaya yönelik açık **Web siteleri** klasörü, tek tek Web sitesini sağ tıklatın ve ardından **özellikleri**.  
  
     **Özellikleri** iletişim kutusu görüntülenir.  
  
7.  Tıklayın **dizin güvenliği** sekmesi.  
  
8.  İçinde **anonim erişim ve kimlik doğrulama denetimi** bölümünde **Düzenle**.  
  
     **Kimlik doğrulama yöntemleri** iletişim kutusu görüntülenir.  
  
9. Altında **kimlik doğrulamalı erişim**seçin **tümleşik Windows kimlik doğrulaması**.  
  
10. Tıklayın **Tamam** kapatmak için **kimlik doğrulama yöntemleri** iletişim kutusu.  
  
11. Tıklayın **Tamam** kapatmak için **özellikleri** iletişim kutusu.  
  
12. Kapat **Internet Information Services** penceresi.  
  
### <a name="to-enable-integrated-windows-authentication-in-windows-vistaiis-7"></a>Windows Vista/IIS 7'de tümleşik Windows kimlik doğrulamasını etkinleştirmek için  
  
1.  Web sunucusunda bir yönetici hesabını kullanarak oturum açın.  
  
2.  Daha önce aşağıdaki adımları izleyerek yapmadıysanız, Windows kimlik doğrulaması ve II6 Yönetim uyumluluğu açın:  
  
    1.  Tıklayın **Başlat**, tıklayın **Denetim Masası** ve ardından **programlar**.  
  
    2.  Altında **programlar ve Özellikler**, tıklayın **kapatma Windows özelliklerini aç veya Kapat**.  
  
         Kullanıcı erişim denetimi iletişim kutusu görünür ve devam etmek izin ister.  
  
    3.  **Devam**'a tıklayın.  
  
         Windows özellikleri iletişim kutusu görüntülenir.  
  
    4.  Özellik listesinde genişletin **Internet Information Services** düğümü.  
  
    5.  Altında **Internet Information Services**, genişletme **World Wide Web Hizmetleri** düğümü.  
  
    6.  Altında **World Wide Web Hizmetleri**, tıklayın **güvenlik**.  
  
    7.  Tıklayın **Windows kimlik doğrulaması**.  
  
    8.  Altında **Internet Information Services**, genişletme **Web yönetimi araçları** düğümü.  
  
    9. Altında **Web yönetimi araçları**, genişletin **IIS 6 Yönetim uyumluluğu** düğüm ve select **IIS 6 metatabanı ve IIS 6 yapılandırma uyumluluğu** onay kutusu.  
  
    10. Altında **Web yönetimi araçları**seçin **IIS Yönetim Konsolu** tıklatıp **Tamam.**  
  
    11. Bu değişikliklerin devreye girmesi bilgisayarı yeniden başlatın.  
  
3.  Tıklayın **Başlat** 'a tıklayarak **Denetim Masası**.  
  
4.  Tıklayın **Klasik Görünüm**ve çift tıklatarak **Yönetimsel Araçlar**.  
  
5.  İçinde **adı** sütun ve çift **Internet Information Services (IIS) Yöneticisi'ni**.  
  
6.  İçinde **bağlantıları** sütun, sunucu düğümünü genişletin.  
  
     A **Web siteleri** klasörü altında sunucu adına açar.  
  
7.  Genişletin **Web siteleri** düğüm ve tümleşik Windows kimlik doğrulamasını etkinleştirmek istediğiniz Web sitesini tıklayın.  
  
8.  Orta bölme başlığının seçtiğiniz Web sitesi adını değiştirir. Bu bölmede altında **IIS** başlığı çift **kimlik doğrulaması**.  
  
     Bölmenin başlığı değişiklikleri **kimlik doğrulaması**.  
  
9. İçinde **kimlik doğrulaması** bölmesinde, **adı** sütun sağ **Windows kimlik doğrulaması** ve ardından **etkinleştirmek**.  
  
10. Kapat **Internet Information Services (IIS) Yöneticisi'ni** penceresi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Web uygulamalarında hata ayıklama: Hatalar ve sorun giderme](../debugger/debugging-web-applications-errors-and-troubleshooting.md)   
 [Microsoft Özet kimlik doğrulaması](http://go.microsoft.com/fwlink/?LinkId=77938)   
 [Windows Vista ile IIS 7.0 Web uygulamaları ve Visual Studio çalıştıran](http://msdn.microsoft.com/library/262a82ac-dd0e-4096-86c6-fb463e88be66)



