---
title: Projeler ve Çözümler, Seçenekler İletişim Kutusu
ms.date: 07/14/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Projects.General
- VS.ToolsOptionsPages.Projects.Locations
helpviewer_keywords:
- Projects and Solutions Options dialog box
- Options dialog box, Projects and Solutions
ms.assetid: 2801f24e-a138-488a-ae3c-e1f99a678ac0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 09881462b0723dc1e601c908efeabc317ed70b69
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388955"
---
# <a name="projects-and-solutions-page-options-dialog-box"></a>Projeler ve çözümler sayfanın, Seçenekler iletişim kutusu

Projeler ve çözümler için ilgili Visual Studio davranışını ayarlar. Bu seçeneklere erişmek için seçin **Araçları** > **seçenekleri**, genişletme **projeler ve çözümler**ve ardından **genel** .

Proje ve şablon klasörleri için varsayılan yolları aracılığıyla ayarlanan **konumları** aynı iletişim kutusundaki sekmesi.

## <a name="general-page"></a>Genel sayfası

Aşağıdaki seçenekler mevcuttur **genel** sayfası.

### <a name="always-show-error-list-if-build-finishes-with-errors"></a>Hata listesi bir derleme hatayla bittiğinde her zaman göster

Açılır **hata listesi** derleme tamamlandığında, yalnızca bir projeyi oluşturmak başarısız olursa penceresi. Derleme işlemi sırasında oluşan hatalar görüntülenir. Bu seçenek işaretli değilse, hataları oluşmaya ancak yapı tamamlandığında pencerenin açılmaz. Bu seçenek varsayılan olarak etkindir.

### <a name="track-active-item-in-solution-explorer"></a>Çözüm Gezgini'nde etkin öğeyi takip et

Bu onay kutusu seçildiğinde, **Çözüm Gezgini** otomatik olarak açılır ve etkin öğeyi seçili. Seçili öğe değiştikçe, farklı bir proje veya çözüm dosyaları ya da farklı bileşenlerin bir tasarımcıda çalışın. Ne zaman bu seçenek işaretli değilse, seçimdeki **Çözüm Gezgini** otomatik olarak değiştirmez. Bu seçenek varsayılan olarak etkindir.

### <a name="show-advanced-build-configurations"></a>Gelişmiş derleme yapılandırmalarını Göster

Bu onay kutusu seçildiğinde, derleme yapılandırma seçenekleri görünür **proje özellik sayfaları** iletişim kutusu ve **çözüm özellik sayfaları** iletişim kutusu. Yapı yapılandırma seçeneklerini üzerinde görünmez temizlendiğinde **proje özellik sayfaları** iletişim kutusu ve **çözüm özellik sayfaları** Visual Basic için iletişim kutusu ve C# bir içeren projeleri yapılandırma veya iki yapılandırması hata ayıklama ve yayın. Kullanıcı tanımlı bir yapılandırma bir proje varsa, yapı yapılandırma seçenekleri gösterilmektedir.

Seçili üzerinde olmadığında komutları **derleme** menüsünde gibi **Çözümü Derle**, **çözümü yeniden derle**, ve **çözümü Temizle**, olan Yayın yapılandırması ve komutları üzerinde gerçekleştirilen **hata ayıklama** menüsünde gibi **hata ayıklamayı Başlat** ve **hata ayıklama olmadan Başlat**, gerçekleştirilir hata ayıklama yapılandırması.

### <a name="always-show-solution"></a>Çözümü her zaman göster

Bu onay kutusu seçildiğinde, çözüm ve çözümler üzerinde çalışan tüm komutları her zaman IDE'de gösterilir. Bu onay kutusu temizlenirse, tüm projeler tek başına bir proje olarak oluşturulur ve çözümü yalnızca bir proje içeriyorsa, Çözüm Gezgini veya hareket komutları çözümde IDE'de çözümler üzerinde görmezsiniz.

### <a name="save-new-projects-when-created"></a>Oluşturulduğunda yeni projeleri Kaydet

Bu onay kutusu seçildiğinde, projeniz için bir konum belirtebilirsiniz **yeni proje** iletişim kutusu. Bu onay kutusu temizlenirse, tüm yeni projeler geçici proje olarak oluşturulur. Geçici projeler ile çalışırken, oluşturabilir ve bir disk konumu belirtmek zorunda kalmadan bir proje ile denemeler yapın.

### <a name="warn-user-when-the-project-location-is-not-trusted"></a>Proje konumu güvenilir olmadığında kullanıcıyı uyarır.

Yeni bir proje oluşturun veya tam olarak (örneğin, bir UNC yolu veya HTTP yolu) güvenli olmayan bir konumda mevcut bir projeyi açmayı denerseniz, bir ileti görüntülenir. İleti oluşturmak veya tam olarak güvenilmeyen bir konumda bir projeyi açmayı denemek her zaman görüntülenip görüntülenmeyeceğini belirtmek için bu seçeneği kullanın.

### <a name="show-output-window-when-build-starts"></a>Derleme başladığında çıkış penceresini göster

Otomatik olarak görüntüler [çıkış penceresine](../../ide/reference/output-window.md) çözümünün gizliliğe IDE içinde oluşturur.

### <a name="prompt-for-symbolic-renaming-when-renaming-files"></a>Sembolik yeniden adlandırmayı olduğunda yeniden adlandırmayı sor

Seçili olduğunda, Visual Studio, aynı zamanda projedeki tüm başvuruları kod öğesine adlandırmalısınız olup olmadığını soran bir ileti kutusu görüntüler.

### <a name="prompt-before-moving-files-to-a-new-location"></a>Dosyaları yeni bir konuma taşımadan önce sor

Dosya konumları eylemler tarafından değiştirilmeden önce seçili olduğunda, Visual Studio onaylama ileti kutusu görüntüler **Çözüm Gezgini**.

### <a name="reopen-documents-on-solution-load"></a>Çözüm yükü'ndeki belgeleri yeniden Aç

**Yeni Visual Studio 2017 sürüm 15,8 önizleme 2 ve üzeri**

Çözüm açıldığında seçili olduğunda, çözümün önceki bir zamana kapatıldı açık bırakıldı belgeleri otomatik olarak açılır.

Belirli türde dosya ve tasarımcılar yeniden açmayı çözüm yükü gecikmeye yol açabilir. İçin bu seçeneğin işaretini [çözüm yükleme performansını iyileştirmek](../../ide/visual-studio-performance-tips-and-tricks.md#disable-automatic-file-restore) çözümün önceki bağlamı geri yüklemek istemiyorsanız.

## <a name="locations-page"></a>Konumları sayfası

Aşağıdaki seçenekler mevcuttur **konumları** sayfası.

### <a name="projects-location"></a>Projeleri konumu

Burada Visual Studio yeni proje ve çözüm klasörleri oluşturur. varsayılan konumu belirtir. Birçok iletişim kutusu da başlangıç noktaları klasörü için bu seçeneği ayarlamak konumu kullanın. Örneğin, **Proje Aç** iletişim kutusu için bu konumu kullanır **Projelerim** kısayol.

### <a name="user-project-templates-location"></a>Kullanıcı proje şablonları konumu

Varsayılan konumu belirtir, **yeni proje** iletişim kutusu listesini oluşturmak için kullandığı **Şablonlarım**. Daha fazla bilgi için [nasıl yapılır: bulun ve düzenleme şablonlarını](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

### <a name="user-item-templates-location"></a>Kullanıcı öğe Şablonları konumu

Varsayılan konumu belirtir, **Yeni Öğe Ekle** iletişim kutusu listesini oluşturmak için kullandığı **Şablonlarım**. Daha fazla bilgi için [nasıl yapılır: bulun ve düzenleme şablonlarını](../../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Seçenekler iletişim kutusu, projeler ve çözümler, derleme ve çalıştırma](../../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Seçenekler İletişim Kutusu, Projeler ve Çözümler, Web Projeleri](../../ide/reference/options-dialog-box-projects-and-solutions-web-projects.md)
