---
title: Özellik sayfaları, JavaScript | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 586ad4352dfdf88aef87d4f9c815a776f85a6a82
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49904199"
---
# <a name="property-pages-javascript"></a>Özellik Sayfaları, JavaScript
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
**Özellik sayfaları**proje ayarlarına erişim sağlar. Görüntülenen sayfaları kullanabilirsiniz **özellik sayfaları** proje özelliklerini değiştirmek için.  
  
 Proje özelliklerine erişmek için bir proje düğümü seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.  
  
 [!INCLUDE[note_settings_general](../../includes/note-settings-general-md.md)]  
  
 Aşağıdaki sayfalar ve seçenekleri görünür **özellik sayfaları**.  
  
## <a name="configuration-and-platform-page"></a>Yapılandırma ve Platform sayfası  
 Görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmek için aşağıdaki seçenekleri kullanın.  
  
 **Yapılandırma**  
 Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**, **yapılandırmalarında**, veya kullanıcı tarafından tanımlanan bir yapılandırmadır. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
 **Platform**  
 Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Ayarlar **herhangi bir CPU** (için varsayılan [!INCLUDE[win8_appname_long](../../includes/win8-appname-long-md.md)] uygulamaları), **x64**, **ARM**, **x86**, veya kullanıcı tarafından tanımlanan bir platformdur. Daha fazla bilgi için [hata ayıklama ve dağıtım proje yapılandırmalarını](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e).  
  
## <a name="general-page"></a>Genel sayfası  
 Projenin genel özellikler ayarlamak için aşağıdaki seçenekleri kullanın.  
  
> [!NOTE]
>  Bazı seçenekler yalnızca Windows Store uygulamalarında kullanılabilir.  
  
 **Çıkış yolu**  
 Projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Yol görelidir; mutlak bir yol girerseniz, mutlak yol projeye kaydedilir. Bin\Debug varsayılan yoldur.  
  
 Basitleştirilmiş yapı yapılandırmaları kullandığınızda, proje sistemi bir hata ayıklama sürüm yayını mı belirler. Tıkladığınızda **hata ayıklama**, **hata ayıklamayı Başlat** (veya F5 tuşuna basın) derleme, hata ayıklama konumuna koyar koymak **çıkış yolu** belirtirsiniz. Ancak, **Çözümü Derle** komutunu **derleme** menü, belirttiğiniz konuma koyar. Menü çubuğunda, Gelişmiş derleme yapılandırmalarını etkinleştirmeyi tercih **Araçları**, **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**seçin **genel**ve ardından temizlemek **Show Gelişmiş derleme yapılandırmaları**onay kutusu. Bu, tüm yapılandırma değerleri üzerinde el ile denetim ve hata ayıklama veya sürüm sürümü olup olmadığını oluşturulmuştur sağlar. Daha fazla bilgi için [NIB: Genel, projeler ve çözümler, Seçenekler iletişim kutusu](http://msdn.microsoft.com/en-us/8f8e37e8-b28d-4b13-bfeb-ea4d3312aeca).  
  
 **Varsayılan dil**  
 Projenin varsayılan dilini belirtir. Seçilen dil seçeneği **saat, dil ve bölge** Denetim Masası'nda kullanıcının tercih edilen dili belirtir. Proje için varsayılan dil belirleyerek kullanıcının tercih ettiği dil uygulamada sağlanan dil kaynaklarıyla eşleşmiyorsa belirtilen varsayılan dil kaynaklarını kullanıldığından emin olun.  
  
## <a name="debug-page"></a>Hata ayıklama sayfası  
 Davranış projesinde hata ayıklama özelliklerini ayarlamak için aşağıdaki seçenekleri kullanın.  
  
> [!NOTE]
>  Bazı seçenekler yalnızca Windows Store uygulamalarında kullanılabilir.  
  
 **Hata ayıklayıcıyı başlatmak için**  
 Hata ayıklayıcı için varsayılan ana bilgisayar belirtir.  
  
- Seçin **yerel makine** Visual Studio ana bilgisayarda uygulamayı başlatmak için. Daha fazla bilgi için [yerel makine üzerinde çalışan uygulamalar](http://go.microsoft.com/fwlink/?LinkId=234912).  
  
- Seçin **simülatör** Simulator'da uygulamayı başlatmak için. Daha fazla bilgi için [uygulamaları simülatörde çalıştırılan](http://go.microsoft.com/fwlink/?LinkId=234913).  
  
- Seçin **uzak makine** uzak bir bilgisayarda uygulamayı başlatmak için. Uzaktan hata ayıklama hakkında daha fazla bilgi için bkz. [uzak makinede çalışan uygulamalar](http://go.microsoft.com/fwlink/?LinkId=234914).  
  
  **Uygulamayı Başlat**  
  F5 tuşuna basın veya tıklayın uygulamanın başlatılıp başlatılmayacağını belirtir **hata ayıklama**, **hata ayıklamayı Başlat**. Seçin **Evet** için uygulamayı başlatın; Aksi takdirde seçin **Hayır**. Seçerseniz **Hayır**, başlatmak için farklı bir yöntem kullanıyorsanız yine de uygulamayı ayıklayabilirsiniz.  
  
  **Hata ayıklayıcı türü**  
  Hata ayıklanacak kod türlerini belirtir. Seçin **yalnızca betik** JavaScript kod hatası ayıklamak için. Seçin **yalnızca yönetilen** ortak dil çalışma zamanı tarafından yönetilen kodda hata ayıklamak için. Seçin **yalnızca yerel** C++ kod hatalarını ayıklamak için. Seçin **betik ile yerel** C++ ve JavaScript hata ayıklama. Seçin **(yönetilen ve yerel) karışık** yönetilen hatasını ayıklamak ve C++ kodu.  
  
  **Yerel ağ geri döngüsüne izin ver**  
  Uygulamayı test etmek için IP Geridöngü adresine erişime izin verilip verilmediğini belirtir. Seçin **Evet** istemci uygulaması aynı makinede ise, aksi takdirde çalışan sunucu uygulaması olduğu geri döngü adresinin kullanımına izin vermek için seçin **Hayır**. Bu özellik yalnızca **başlatmak için hata ayıklayıcı** özelliği **uzak makine**.  
  
  **Makine adı**  
  Hata ayıklayıcıyı barındıracak uzak bilgisayarın adını belirtir. Bu özellik yalnızca **başlatmak için hata ayıklayıcı** ayarlanır **uzak makine**.  
  
  **Kimlik doğrulaması gerektir**  
  Uzak bilgisayarın kimlik doğrulaması gerektirip gerektirmediğini belirtir. Bu özellik yalnızca **başlatmak için hata ayıklayıcı** ayarlanır **uzak makine**.



