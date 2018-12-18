---
title: 'Nasıl yapılır: ASP.NET uygulamaları için hata ayıklamayı etkinleştirme | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications
- Web.config configuration file, debug mode
- debugging [Visual Studio], ASP.NET
ms.assetid: 3beed819-cece-4864-8184-bd410000973a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c199e03af8a21b3134ae0e2afac7bd9b153be2f4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749126"
---
# <a name="how-to-enable-debugging-for-aspnet-applications"></a>Nasıl Yapılır: ASP.NET Uygulamaları için Hata Ayıklamayı Etkinleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklamayı etkinleştirmek için hem de etkinleştirmelisiniz **proje özellikleri** sayfasında ve uygulamanın web.config dosyasında.  
  
> [!NOTE]  
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir. Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü. Daha fazla bilgi için [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-aspnet-debugging-in-the-project-properties-visual-basicc"></a>Proje özelliklerinde ASP.NET hata ayıklamayı etkinleştirmek için (Visual Basic / C#)  
  
1.  İçinde **Çözüm Gezgini**, bir Web projesinin adını sağ tıklatın ve seçin **özellikleri**.  
  
2.  Proje özellikleri sayfasında tıklayın **Web** sekmesi.  
  
3.  Altında **hata ayıklayıcıları**seçin **ASP.NET** onay kutusu.  
  
### <a name="to-enable-debugging-in-the-webconfig-file"></a>Web.config dosyasında hata ayıklamayı etkinleştirmek için  
  
1.  Herhangi standart bir metin düzenleyicisi veya XML ayrıştırıcısını kullanarak web.config dosyasını açın.  
  
    > [!NOTE]  
    > Ancak, bir Web tarayıcısı kullanarak dosyaya uzaktan erişemezsiniz. Güvenlik nedenleriyle, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], Microsoft IIS'i Web.config dosyalarına doğrudan tarayıcı erişimini engellemeye yardımcı olacak şekilde yapılandırır. Bir tarayıcı kullanarak bir yapılandırma dosyasına erişmeye çalışırsanız, HTTP erişim hatası 403 (yasak) alırsınız.  
  
2.  Web.config bir XML dosyasıdır ve bu yüzden etiketlerle işaretlenmiş iç içe yerleştirilmiş bölümler içerir. Bulun `configuration/system.web/compilation` öğesi. Derleme ögesi yoksa, onu oluşturun.  
  
3.  `compilation` öğesi bir `debug` özniteliği içermiyorsa, özniteliği öğeye ekleyin.  
  
4.  `debug` öznitelik değerinin `true`olarak ayarlandığından emin olun.  
  
Web.config dosyası, aşağıdaki örnek gibi görünmelidir. Yapılandırma ve system.web öğeleri arasında bölümler olabileceğini unutmayın  
  
-   yapılandırma ve system.web öğeleri arasındaki öğe bölümleri  
  
-   system.web ve derleme öğeleri arasındaki öğe bölümleri  
  
-   Derleme ögesi, diğer öznitelikleri ve öğeleri içerebilir.  
  
## <a name="example"></a>Örnek  
  
```  
<configuration>  
    ...  
    <system.web>  
        <compilation  
            debug="true"  
            ...  
        >  
        ...  
        </compilation>  
    </system.web>  
</configuration>  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
[!INCLUDE[vstecasp](../includes/vstecasp-md.md)], Web.config dosyalarına yapılan değişiklikleri otomatik olarak algılar ve yeni yapılandırma ayarlarını uygular. Değişikliklerin etkili olması IIS sunucusunu yeniden başlatın veya bilgisayarı yeniden başlatmanız gerekmez.  
  
Bir Web sitesi birden çok sanal dizin ve alt dizinler içerebilir ve her birinde Web.config dosyaları bulunabilir. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamaları, URL yolunda daha yüksek düzeylerde Web.config dosyalarından ayarları miras alabilir. Hiyerarşik yapılandırma dosyaları, aynı anda çeşitli [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamalarının ayarlarını değiştirmenize olanak tanır, örneğin hiyerarşide onun altındaki tüm uygulamalar için. Ancak, `debug`, hiyerarşide daha düşük bir dosyada ayarlanırsa, daha yüksek değeri geçersiz kılar.  
  
Örneğin, `debug="true"`özelliğini, www.microsoft.com/aaa/Web.config üzerinde belirtebilirsiniz ve aaa klasöründe veya aaa klasörünün herhangi bir alt klasöründeki herhangi bir uygulama bu ayarı miras alır. Bu yüzden, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamanız www.microsoft.com/aaa/bbb konumundaysa, o ve www.microsoft.com/aaa/ccc, www.microsoft.com/aaa/ddd ve benzeri içindeki herhangi bir [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulaması o ayarı miras alacaktır. Tek istisna durum, bu uygulamalardan biri kendi alt Web.config dosyasını kullanarak ayarı geçersiz kılarsa söz konusudur.  
  
Hata ayıklama modunu etkinleştirme, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] uygulamanızın performansını önemli ölçüde etkiler. Bir yayınlama uygulaması dağıtmadan veya performans ölçümleri gerçekleştirmeden önce, hata ayıklama modunu devre dışı bırakmayı unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
[ASP.NET ve AJAX Uygulamalarında Hata Ayıklama](../debugger/debugging-aspnet-and-ajax-applications.md)  
  




