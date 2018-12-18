---
title: ClickOnce uygulamalarını yayımlama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options
- Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- ClickOnce applications, publishing
- applications [Visual Studio], ClickOnce deployment
- deploying applications [ClickOnce], publishing ClickOnce applications
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: 4282ce38671e2270c1e91d70df8968d790c54a22
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49891771"
---
# <a name="publishing-clickonce-applications"></a>ClickOnce Uygulamalarını Yayımlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Yayımlama sırasında bir [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] ilk kez uygulama yayımlama özellikleri Yayımlama Sihirbazı'nı kullanarak ayarlayabilirsiniz. Yalnızca birkaç özellikleri Sihirbazı'nda bulunur; diğer tüm özellikleri varsayılan değerlerine ayarlanır.  
  
 Üzerinde yapılan özelliklerini yayımlamak için sonraki değişiklikler **Yayımla** sayfasını **Proje Tasarımcısı**.  
  
## <a name="publish-wizard"></a>Yayımlama Sihirbazı  
 Uygulamanızı yayımlamak için temel ayarları ayarlamak için Yayımla Sihirbazı'nı kullanabilirsiniz. Bu, yayımlama aşağıdaki özellikleri içerir:  
  
- Yayımlama klasörü konumu - Visual Studio (yerel bilgisayar, ağ dosya paylaşımı, FTP sunucusu veya Web sitesi) dosyaları burada kopyalar  
  
- Yükleme klasörü konumu - son kullanıcıların yükleme yapacakları (ağ dosya paylaşımı, FTP sunucusu, Web sitesi, CD/DVD kaynağı)  
  
- Çevrimiçi veya çevrimdışı kullanılabilirliği - son kullanıcıların uygulama ile veya bir ağ bağlantısı olmadan erişebilir.  
  
- Güncelleştirme sıklığı - ne sıklıkta uygulama için yeni güncelleştirmeleri denetler.  
  
  Daha fazla bilgi için [nasıl yapılır: yayımlama sihirbazını kullanarak ClickOnce uygulaması yayımlama](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## <a name="publish-page"></a>Yayımlama Sayfası  
 **Yayımla** sayfasının **Proje Tasarımcısı** ClickOnce dağıtım özelliklerini yapılandırmak için kullanılır. Aşağıdaki tabloda konularını listeler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: Visual Studio'nun Dosyaları Nereye Kopyalayacağını Belirtme](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Visual Studio bildirimleri ve uygulama dosyalarını nerede koyar ayarlama işlemi açıklanmaktadır.|  
|[Nasıl yapılır: Son Kullanıcıların Yükleme Yapacakları Konumu Belirtme](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Kullanıcılar uygulamayı indirmek ve yüklemek için nereye konumu ayarlama işlemi açıklanmaktadır.|  
|[Nasıl yapılır: ClickOnce Çevrimdışı veya Çevrimiçi Yükleme Modunu Belirtme](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Uygulama çevrimiçi veya çevrimdışı kullanılabilir olup olmadığını ayarlama işlemi açıklanmaktadır.|  
|[Nasıl yapılır: ClickOnce Yayım Sürümü'nü Ayarlama](../deployment/how-to-set-the-clickonce-publish-version.md)|ClickOnce ayarlama işlemi açıklanmaktadır **yayımlama sürümü** özelliği yayımlamakta olduğunuz uygulamayı güncelleştirme olarak kabul edilip edilmeyeceğini belirler.|  
|[Nasıl yapılır: ClickOnce Yayım Sürümünü Otomatik Olarak Artırma](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Düzeltme numarasını otomatik artış açıklar **PublishVersion** her zaman uygulama yayımlayın.|  
  
 Daha fazla bilgi için [yayımlama sayfası, Proje Tasarımcısı](../ide/reference/publish-page-project-designer.md)  
  
### <a name="application-files-dialog-box"></a>Uygulama dosyaları iletişim kutusu  
 Bu iletişim kutusu, projenizdeki dosyaları yayımlama, dinamik indiriliyor ve güncelleştiriliyor kategorilendirilmiş belirtmenize olanak sağlar. Bu, varsayılan olarak dışlanmamış veya yükleme grubu olan proje dosyaları listeleyen bir kılavuz içerir.  
  
 Dosyaları hariç tutmak, veri dosyalarını veya önkoşul işaretlemek dosyaları ve Visual STUDİO'da koşullu yüklemesi için dosya grupları oluşturmak için bkz [nasıl yapılır: belirtin, dosyaları yayımlanır ClickOnce tarafından](../deployment/how-to-specify-which-files-are-published-by-clickonce.md). Mage.exe kullanarak, veri dosyalarını da işaretleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasına bir veri dosyası dahil](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### <a name="prerequisites-dialog-box"></a>Önkoşullar İletişim Kutusu  
 Yüklendiklerinde nasıl hangi önkoşul bileşenlerinin de yüklüyse, bu iletişim kutusunu belirtir. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) ve [Önkoşullar iletişim kutusu](../ide/reference/prerequisites-dialog-box.md).  
  
### <a name="application-updates-dialog-box"></a>Uygulama güncelleştirmeleri iletişim kutusu  
 Bu iletişim kutusunda, uygulama yükleme güncelleştirmeleri nasıl denetleyeceğini belirtir. Daha fazla bilgi için [nasıl yapılır: ClickOnce uygulaması için güncelleştirmeleri yönetme](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### <a name="publish-options-dialog-box"></a>Yayımla iletişim kutusu seçenekleri  
 Yayımlama Seçenekleri iletişim kutusu, bir uygulamanın dağıtım seçeneklerini belirtir.  
  
|||  
|-|-|  
|[Nasıl yapılır: ClickOnce Uygulaması için Yayımlama Dilini Değiştirme](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Bir dil ve kültür yerelleştirilmiş sürümüyle eşleşecek şekilde nasıl belirtileceğini açıklar.|  
|[Nasıl yapılır: ClickOnce Uygulaması için Başlat Menüsü Adı Belirtme](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|ClickOnce uygulaması için görünen adını değiştirmek açıklar.|  
|[Nasıl yapılır: Teknik Destek için bir Bağlantı Belirtme](../deployment/how-to-specify-a-link-for-technical-support.md)|Nasıl ayarlanacağı açıklanır **destek URL'si** özelliği bir Web sayfası veya kullanıcılar nereye uygulama hakkında bilgi almak için dosya paylaşımı tanımlar.|  
|[Nasıl yapılır: Bir ClickOnce Dağıtımı'nda Bağımsız Önkoşullar için Destek URL'sini Belirtme](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|El ile her önkoşul destek URL'lerini dahil etmek için bir uygulama bildirimi alter göstermişti.|  
|[Nasıl yapılır: ClickOnce Uygulaması için bir Yayımlama Sayfası Belirtme](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Oluşturma ve yayımlama uygulama ile birlikte varsayılan Web sayfası (publish.htm) açıklanır|  
|[Nasıl yapılır: ClickOnce Varsayılan Web Sayfasını Özelleştirme](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Otomatik olarak oluşturulur ve uygulama ile birlikte yayımlanan Web sayfasında özelleştirmeyi açıklar.|  
|[Nasıl yapılır: CD Yüklemeleri için AutoStart'ı Etkinleştirme](../deployment/how-to-enable-autostart-for-cd-installations.md)|AutoStart'ı etkinleştirin; böylelikle medya eklendiğinde, ClickOnce uygulamasını otomatik olarak başlatıldığını açıklar.|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Nasıl yapılır: ClickOnce Uygulaması için Dosya İlişkilendirmeleri Oluşturma](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|ClickOnce uygulaması için dosya adı uzantısı desteği eklemeyi açıklar.|  
|[Nasıl yapılır: Çevrimiçi bir ClickOnce Uygulamasında Sorgu Dize Bilgilerini Alma](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Bir ClickOnce uygulamasını çalıştırmak için kullanılan URL içinde geçirilen parametrelerin nasıl alınacağını gösterir.|  
|[Nasıl yapılır: Tasarımcıyı Kullanarak ClickOnce Uygulamalarında URL Etkinleştirmeyi Devre Dışı Bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Uygulamayı başlatmak için zorlama açıklar **Başlat** Tasarımcısını kullanarak menüsü.|  
|[Nasıl yapılır: ClickOnce Uygulamalarında URL Etkinleştirmeyi Devre Dışı Bırakma](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Uygulamayı başlatmak için zorlama açıklar **Başlat** menüsü.|  
|[İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Yalnızca ilk Tasarımcısı'nı kullanarak uygulama tarafından kullanıldıklarında uygulama derlemeleri indirileceğini açıklar.|  
|[İzlenecek yol: ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Yalnızca ilk uygulama tarafından kullanıldıklarında uygulama derlemeleri indirileceğini açıklar.|  
|[İzlenecek yol: ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Uydu derlemelerini isteğe bağlı olarak işaretler ve bir istemci makinesi, geçerli kültür ayarları için ihtiyaç duyduğu derlemeyi indirmek açıklar.|  
|[İzlenecek yol: ClickOnce Uygulamasını El ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|ClickOnce uygulamanızı dağıtmak için .NET Framework yardımcı programları kullanmayı açıklar.|  
|[İzlenecek yol: Yeniden İmzalama Gerektirmeyen ve Marka Bilgisini Koruyan bir ClickOnce Uygulamasını El ile Dağıtma](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)|.NET Framework yardımcı programları bildirimlerini yeniden imzalama olmadan ClickOnce uygulamanızı dağıtmak için nasıl kullanılacağını açıklar.|  
|[NIB: Nasıl yapılır: bir uygulama belirli bir CPU türü için en iyi duruma getirme](http://msdn.microsoft.com/en-us/294a75d2-4279-4b72-8298-2bea05be907a)|Bir 64-bit işlemci için değiştirerek yayımlama **hedef CPU** veya **Platform hedefi** projenizdeki özellik.|  
|[İzlenecek yol: ClickOnce uygulaması birden çok .NET Framework sürümleri üzerinde çalıştırmak etkinleştirme](http://msdn.microsoft.com/en-us/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Yükleme ve'NET Framework'ün birden çok sürümünde çalışan bir ClickOnce uygulamasını etkinleştirmeyi açıklar.|  
|[İzlenecek Yol: ClickOnce Uygulaması için Özel bir Yükleyici Oluşturma](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Bir ClickOnce uygulamasını yüklemek için özel bir yükleyici oluşturma açıklanır.|  
|[Nasıl yapılır: Görsel Stiller Etkinken WPF Uygulaması Yayımlama](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Görsel stillerin etkin kıldığı bir WPF uygulamasını yayımlamak istediğinizde görüntülenen bir hatayı gidermek için adım adım yönergeler sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Başvurusu](../deployment/clickonce-reference.md)



