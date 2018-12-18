---
title: SharePoint uygulamaları için performans profili oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 67623989fc8ff2bf2d44bc435a48db81fecb1fba
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44282347"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>SharePoint uygulamaları için performans profili

SharePoint uygulamalarınız yavaş veya verimsiz çalışıyorsa, sorunlu kod ve diğer öğeleri tanımlamak için Visual Studio profil oluşturma özelliklerini kullanabilirsiniz. Yük testi özelliğini kullanarak bir SharePoint uygulaması zaman birçok kullanıcının aynı anda uygulamaya erişim gibi stres altında nasıl performans gösterdiğini belirleyebilirsiniz. Web performans testlerini çalıştırarak uygulamanın web üzerinde nasıl çalıştığını ölçebilirsiniz. Kodlanmış UI testleri kullanarak kullanıcı arabirimi de dahil olmak üzere tüm SharePoint uygulaması için doğru şekilde işleyip işlemediğini doğrulayabilirsiniz. Bu testleri birlikte kullandığınızda, bunlar Uygulamanızı dağıtmadan önce performans sorunlarını belirlemenize yardımcı olabilir.

## <a name="profile-tools-overview"></a>Profil araçlarına genel bakış

Profil oluşturma gözleme ve çalışırken uygulamanızın performans davranışını kaydetme işlemini gösterir. Uygulamanızın profilini oluşturmanız, performans sorunlarını, verimsiz kod ve uygulamaların yavaş çalışmasına veya çok fazla bellek kullanmasına neden bellek ayırma sorunları gibi sorunları ortaya çıkarabilirsiniz. Örneğin, kodunuzda sıkça çağrılan ve uygulamanızın genel performansını yavaşlatabilecek öğeleridir sıcak tanımlamak için profil oluşturma kullanabilirsiniz. Etkin notlalar tanımladıktan sonra genellikle iyileştirebilir veya bunları ortadan kaldırın.

Tanımlamak ve bu tür performans sorunlarını bulmak için tümleşik geliştirme ortamında (IDE) birden fazla profil aracı kullanabilirsiniz. Bu araçlar, diğer Visual Studio Proje türleri için yaptıkları gibi SharePoint projeleri için aynı şekilde çalışır. Profil oluşturma araçları performans Sihirbazı belirttiğiniz testleri kullanan bir performans oturumu oluşturulmasını adım yol gösterir. Performans oturumu bir veya daha fazla profil oluşturma çalıştırma sonuçlarını birlikte bir uygulamadan performans bilgileri toplarken kullanılan yapılandırma verileri kümesidir. Performans oturumları, proje klasörünüzde depolanır ve bunları görüntüleyebilirsiniz **performans Gezgini**. Daha fazla bilgi için [anlama performans koleksiyon metotları](/visualstudio/profiling/understanding-performance-collection-methods).

Oluşturma ve uygulamanızda profil çözümlemesi çalıştırma sonra bir rapor performansı hakkında ayrıntılar sağlar. Bu rapor, zaman, hiyerarşik işlev çağrı yığını veya çağrı ağacı CPU kullanımının grafiği gibi öğeleri içerebilir. Raporun tam içeriği, örnekleme veya Araçlar gibi çalıştırdığınız test türüne bağlı olarak değişebilir. Daha fazla bilgi için [profil oluşturma araçları rapor genel bakışı](http://go.microsoft.com/fwlink/?LinkId=224689).

## <a name="performance-session-process"></a>Performans oturum işlemi

Bir uygulama profili oluşturmak için bir performans oturumu oluşturmak için profil oluşturma araçları performans Sihirbazı kullanarak başlatın. Menü çubuğunda, **Çözümle**, **performans Sihirbazını Başlat**. Sihirbazı tamamladığınızda istediğiniz profil yöntemi ve profil oluşturmak istediğiniz uygulama gibi performans oturumunuza için gereken bilgileri girin. Daha fazla bilgi için [nasıl yapılır: performans Sihirbazı'nı bir Web sitesi veya Web uygulaması kullanarak profil](http://go.microsoft.com/fwlink/?LinkId=224692). Alternatif olarak, ayarlamak ve performans oturumu çalıştırmak için komut satırı seçeneklerini kullanabilirsiniz. Daha fazla bilgi için [satırından profil oluşturma araçları kullanarak](http://go.microsoft.com/fwlink/?LinkId=224703). Performans oturumunu her yönüyle el ile yapılandırmak istiyorsanız, bkz. [nasıl yapılır: el ile performans oturumu oluşturma profil oluşturma araçları ile](http://go.microsoft.com/fwlink/?LinkId=224691). Performans oturumu, birim testinden içinde oluşturabilirsiniz **Test sonuçları** birim testi için kısayol menüsünü açarak ve ardından penceresinde **başarım oturumu Oluştur**.

Performans oturumunu ayarladıktan ayarladıktan sonra oturum yapılandırmasını kaydettikten, profil oluşturma verilerini sağlamak için yapılandırılmış ve uygulamayı çalıştırır. Uygulamayı kullanırken performans verileri günlük dosyasına yazılır. Performans oturumları listelenir **performans Gezgini** altında **hedefleri** klasör. Bir performans oturumu sona erdikten sonra rapor görünür **raporları** klasöründe **performans Gezgini**. Raporu görüntülemek için projeyi açın **performans Gezgini**. Bir performans oturumunun özelliklerini görüntülemek veya yapılandırmak için kısayol menüsünü açın. **performans Gezgini**ve ardından **özellikleri**. Performans oturumu özellikleri hakkında daha fazla bilgi için bkz. [profil oluşturma araçları için performans oturumları yapılandırma](http://go.microsoft.com/fwlink/?LinkId=224694). Performans oturumu sonuçlarını yorumlama hakkında daha fazla bilgi için bkz: [profil oluşturma araçları verilerini analiz etme](http://go.microsoft.com/fwlink/?LinkId=224704).

## <a name="stress-test"></a>Stres testi

Visual Studio'da yük testleri ve web performans testleri oluşturarak, uygulamalarınızı stres performansını çözümleyebilirsiniz. Visual Studio'da yükleme testi oluşturduğunuzda, uygulamanızı test etmek için senaryo olarak adlandırılan bir dizi etkene birlikte belirtin. Bu etkenler, yük düzeni, test karışımı modeli, test karışımı, ağ karışımı ve web tarayıcısı karışımını içerir. Yük testi senaryoları hem birim testleri ve web başarım testleri içerebilir.

Şekil 1: örnek yükleme testi sonuçları

![Yük testi grafikler görünümü](../sharepoint/media/load-webgraphs.png "çalışan yük testine grafikler görünümü")

Web performans testleri, bir son kullanıcının SharePoint uygulamasıyla nasıl etkileştiğinin benzetimini yapar. HTTP istekleri tarayıcı oturumu kaydetme veya kullanılarak web performansı testlerini oluşturabilirsiniz **Web Performans Testi Kaydedicisi**. Web istekleri görünür **Web Performans Testi Düzenleyicisi** tarayıcı oturumu sona erdikten sonra. Ardından sonuçlarda ayıklayabilirsiniz **Web Performans Test Sonuçları Görüntüleyicisi**. Kullanarak web performans testleri el ile oluşturabilirsiniz **Web Performans Testi Düzenleyicisi**.

## <a name="test-user-interfaces"></a>Test kullanıcı arabirimleri

Kodlanmış UI testleri, SharePoint uygulamanızın kullanıcı arabirimi (UI) otomatik olarak yönlendirir. Bu testler, düğmeler ve menüler, düzgün şekilde çalıştıklarını doğrulamak için gibi kullanıcı Arabirimi denetimleri kapsar. Doğrulama veya başka bir mantık kullanıcı Arabiriminde gibi bir web sayfasında gerçekleştirilirse bu tür sınama özellikle yararlıdır. Kodlanmış UI testleri, el ile testleri otomatik hale getirmek için de kullanabilirsiniz. Diğer uygulama türleri için testleri oluştururken oluşturma, kodlanmış UI testleri, SharePoint uygulamaları için aynı şekilde. Daha fazla bilgi için [kodlanmış UI testleriyle SharePoint 2010 uygulamalarını test etme](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests).

## <a name="related-topics"></a>İlgili konular

|Başlık|Açıklama|
|-----------|-----------------|
|[İzlenecek yol: bir SharePoint uygulama profili](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|SharePoint uygulamasında örnekleme profili çözümlemesinin gerçekleştirmek nasıl gösterir.|
|[Serbest bırakmadan önce uygulamanızın performansını test etme](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts)|SharePoint uygulamalarında zorlama testi yardımcı olan yük testleri oluşturmayı açıklar.|
|[Kodunuza Birim Testi Uygulama](/visualstudio/test/unit-test-your-code)|Birim testler kullanılarak kodunuzda mantık hataları bulmak açıklar.|
|[Kodlanmış UI Testleriyle SharePoint 2010 Uygulamalarını Test Etme](/visualstudio/test/testing-sharepoint-2010-applications-with-coded-ui-tests)|SharePoint uygulamanızın kullanıcı arabirimi test açıklar.|

## <a name="see-also"></a>Ayrıca bkz.

[Derleme ve hata ayıklama SharePoint çözümleri](../sharepoint/building-and-debugging-sharepoint-solutions.md)
[kod kalitesini iyileştirmek](/visualstudio/test/improve-code-quality)
