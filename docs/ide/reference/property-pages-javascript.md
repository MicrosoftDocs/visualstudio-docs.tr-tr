---
title: Özellik Sayfaları, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.debugging.debuggertype
- javascript.project.property.debugging.requireauthentication
- javascript.project.property.outputpath
- javascript.project.property.debugging.launchapplication
- javascript.project.property.defaultlanguage
- javascript.project.property.debugging.machinename
- javascript.project.property.debugging.allowlocalnetworkloopback
ms.assetid: a05ab01f-3d5d-4675-a845-eab51807d3a3
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a35ee6d086153adc718a1616c0c8f0c8c606fbb7
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2018
ms.locfileid: "50220036"
---
# <a name="property-pages-javascript"></a>Özellik Sayfaları, JavaScript
**Özellik sayfaları** proje ayarlarına erişim sağlar. Görüntülenen sayfaları kullanabilirsiniz **özellik sayfaları** proje özelliklerini değiştirmek için.

Proje özelliklerine erişmek için bir proje düğümü seçin **Çözüm Gezgini**. Üzerinde **proje** menüsünü tıklatın **özellikleri**.

[!INCLUDE[note_settings_general](../../data-tools/includes/note_settings_general_md.md)]

Aşağıdaki sayfalar ve seçenekleri görünür **özellik sayfaları**.

## <a name="configuration-and-platform-page"></a>Yapılandırma ve Platform sayfası
 Görüntülenecek veya değiştirilecek platform ve yapılandırmayı seçmek için aşağıdaki seçenekleri kullanın.

 **Yapılandırma**

 Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**, **yapılandırmalarında**, veya kullanıcı tarafından tanımlanan bir yapılandırmadır. Daha fazla bilgi için [nasıl yapılır: ayarlama hata ayıklama ve dağıtım yapılandırmalarını Visual Studio'da](../../debugger/how-to-set-debug-and-release-configurations.md).

 **Platform**

 Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Ayarlar **herhangi bir CPU** (için varsayılan [!INCLUDE[win8_appname_long](../../debugger/includes/win8_appname_long_md.md)] uygulamaları), **x64**, **ARM**, **x86**, veya kullanıcı tarafından tanımlanan bir platformdur. Daha fazla bilgi için [nasıl yapılır: ayarlama hata ayıklama ve dağıtım yapılandırmalarını Visual Studio'da](../../debugger/how-to-set-debug-and-release-configurations.md).

## <a name="general-page"></a>Genel sayfası
 Projenin genel özellikler ayarlamak için aşağıdaki seçenekleri kullanın.

> [!NOTE]
> Bazı seçenekler yalnızca UWP uygulamalarında kullanılabilir.


 **Çıkış yolu**

 Projenin yapılandırması için çıkış dosyalarının konumunu belirtir. Yol görelidir; mutlak bir yol girerseniz, mutlak yol projeye kaydedilir. Bin\Debug varsayılan yoldur.

 Basitleştirilmiş yapı yapılandırmaları kullandığınızda, proje sistemi bir hata ayıklama sürüm yayını mı belirler. Tıkladığınızda **hata ayıklama**, **hata ayıklamayı Başlat** (veya F5 tuşuna basın) derleme, hata ayıklama konumuna koyar koymak **çıkış yolu** belirtirsiniz. Ancak, **Çözümü Derle** komutunu **derleme** menü, belirttiğiniz konuma koyar. Menü çubuğunda, Gelişmiş derleme yapılandırmalarını etkinleştirmeyi tercih **Araçları**, **seçenekleri**. İçinde **seçenekleri** iletişim kutusunda **projeler ve çözümler**seçin **genel**ve ardından temizlemek **Show Gelişmiş derleme yapılandırmaları**onay kutusu. Bu, tüm yapılandırma değerleri üzerinde el ile denetim ve hata ayıklama veya sürüm sürümü olup olmadığını oluşturulmuştur sağlar.

 **Varsayılan dil**

 Projenin varsayılan dilini belirtir. Seçilen dil seçeneği **saat, dil ve bölge** Denetim Masası'nda kullanıcının tercih edilen dili belirtir. Proje için varsayılan dil belirleyerek kullanıcının tercih ettiği dil uygulamada sağlanan dil kaynaklarıyla eşleşmiyorsa belirtilen varsayılan dil kaynaklarını kullanıldığından emin olun.

## <a name="debug-page"></a>Hata ayıklama sayfası
 Davranış projesinde hata ayıklama özelliklerini ayarlamak için aşağıdaki seçenekleri kullanın.

> [!NOTE]
> Bazı seçenekler yalnızca UWP uygulamalarında kullanılabilir.


 **Hata ayıklayıcıyı başlatmak için**

 Hata ayıklayıcı için varsayılan ana bilgisayar belirtir.

-   Seçin **yerel makine** Visual Studio ana bilgisayarda uygulamayı başlatmak için. Daha fazla bilgi için [yerel makine üzerinde çalışan uygulamalar](../../debugger/run-windows-store-apps-on-the-local-machine.md).

-   Seçin **simülatör** Simulator'da uygulamayı başlatmak için. Daha fazla bilgi için [uygulamaları simülatörde çalıştırılan](../../debugger/run-windows-store-apps-in-the-simulator.md).

-   Seçin **uzak makine** uzak bir bilgisayarda uygulamayı başlatmak için. Uzaktan hata ayıklama hakkında daha fazla bilgi için bkz. [uzak makinede çalışan uygulamalar](../../debugger/run-windows-store-apps-on-a-remote-machine.md).

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
