---
title: VSIX bildirim Tasarımcısı | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72639c3fbef6b8e297d9e81a7383b2ee8220d896
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796447"
---
# <a name="vsix-manifest-designer"></a>VSIX Bildirim Tasarımcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio uzantısı için yükleme davranışı ayarlayan bir VSIX paket bildirim dosyası, değiştirir.  
  
 **VSIX bildirim Tasarımcısı** temel alınan VSIX şemaya eşler. Her şema öğesi, karşılık gelen bir denetim Tasarımcısı'nda kullanarak ayarlayabilirsiniz. Şeması hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md).  
  
 Açmak için **VSIX bildirim Tasarımcısı**, source.extension.vsixmanifest dosyasını **Çözüm Gezgini**, dosyasını açın. Bildirim Tasarımcısı dosyayı geçerli XML içermiyorsa açılmaz.  
  
> [!NOTE]
>  Paketi oluşturulduğunda Source.extension.vsixmanifest extension.vsixmanifest çıkışı yapılır.  
  
## <a name="uielement-list"></a>UIElement Listesi  
 **VSIX bildirim Tasarımcısı** şemanın en üst düzey bu öğelere karşılık gelen dört bölüm içerir:  
  
- Meta Veriler  
  
- Hedefleri yükle  
  
- Varlıklar  
  
- Bağımlılıkları  
  
  Başlık alanı aşağıdaki denetimleri içerir.  
  
  **Ürün adı**  
  Uzantı adı açıklar.  
  
  **Ürün Kimliği**  
  Bu paket için benzersiz kimlik bilgilerini belirtir.  
  
  **Yazar**  
  Uzantı yazarının adını belirtir.  
  
  **Sürüm**  
  Uzantısı sürüm numarasını belirtir.  
  
  **Meta verileri** sekmesi aşağıdaki denetimleri içerir.  
  
  **Açıklama**  
  Görüntülenecek uzantı metin açıklamasını sağlar **Uzantı Yöneticisi**.  
  
  **Dil**  
  Bildirim metinsel verilere karşılık gelen paket varsayılan dilini belirtir. `Language` Özniteliği aşağıdaki ortak dil çalışma zamanı (CLR) yerel kod kurala için kaynak grupları, örneğin, en-us, en, fr-fr. Varsayılan olarak, nötr değerdir; Bu, paketi tüm Visual Studio dili sürümünde çalışacağı anlamına gelir.  
  
  **Lisans**  
  Var olan kullanıcı lisansı içeren metin dosyası belirtir.  
  
  **Simgesi**  
  Görüntülenecek bir simge içeren grafik dosyası (.png, .bmp, .jpeg, .ico) belirtir **Uzantı Yöneticisi**, varsa bir simge. Simge görüntüsü 32 x 32 piksel olmalıdır veya bu boyutlara yeniden boyutlandırılır. Simge yok belirtilirse, **Uzantı Yöneticisi** varsayılan bir simge kullanılır.  
  
  **Önizleme görüntüsü**  
  Görüntülenecek önizleme görüntüsünü içeren grafik dosyası (.png, .bmp, .jpeg, .ico) belirtir **Uzantı Yöneticisi**, bir önizleme görüntüsü varsa. Önizleme görüntüsü 200 x 200 piksel olmalıdır. Hiçbir önizleme görüntüsü belirtilirse, **Uzantı Yöneticisi** varsayılan bir görüntü kullanır.  
  
  **Etiketleri**  
  Arama ipuçları için kullanılacak metni etiketleri ekler.  
  
  **Sürüm Notları**  
  Sürüm Notları'nı içeren bir dosya (.txt, .rtf) belirtir. Ayrıca sürüm notlarını görüntüleyen bir Web sitesinin URL'sini alır.  
  
  **Başlangıç Kılavuzu**  
  İçeriğin veya uzantısı VSIX paketinde kullanma hakkında bilgi içeren bir dosya (.txt, .rtf) belirtir. Bu kılavuz, uzantı yüklemesi tamamlandığında görünür. Ayrıca Kılavuzu görüntüleyen bir Web sitesinin URL'sini alır.  
  
  **Daha fazla bilgi URL'si**  
  Ürün hakkında ek bilgi içeren bir Web sitesinin URL'sini belirtir.  
  
  **Hedefleri Yükle** sekmesi aşağıdaki denetimleri içerir.  
  
  **Yükleme türü**  
  Listeler **Visual Studio Uzantısı** ve **uzantı SDK'sı** yükleme türlerini hedefleyin. Seçenekler, seçtiğiniz türüne bağlı olarak farklılık gösterir.  
  
  **Visual Studio uzantısı**  
  Listeler **InstallationTarget** öğeleri nasıl paket yüklenebilir ve bu uzantı Visual Studio ürünleri yüklenebilir. Her ürün adı ve sürüm veya sürüm aralığına göre ayrı olarak tanımlanır.  Ürün listesine, değiştirilebilir ve silindi. Ad ve bir ürün sürümüne karşılık gelen **kimliği** ve **sürüm** ilişkili öznitelikleri **InstallationTarget** öğesi.  
  
  **Sürüm aralığı** olduğundan [12.0, 14.0] ve aşağıdaki gösterim kullanır:  
  
- [– dahil olan en düşük sürüm  
  
- ] – dahil olan en yüksek sürüm  
  
- (-özel en düşük sürüm  
  
- ) – özel en yüksek sürüm  
  
- Tek sürüm # - yalnızca belirtilen sürüm  
  
  **Uzantı SDK'sı**  
  Belirli bir ürün ve sürümünüz için kapsamlı olmayan genel bir yükleme belirtir. **Hedef Platform tanımlayıcısı** "hedeflediğiniz Windows," gibi bir platform. **Hedef Platform sürümü** gibi 8.0, hedef platform sürümü. **SDK adı** ve **SDK sürümü** adı ve SDK'sı sürüm numarasını sırasıyla.  
  
  **Bu VSIX tüm kullanıcılar için yüklenir (yüklemede bir yükseltme gerektirir)** onay kutusu  
  Bu onay kutusu seçili değilse, bu uzantı tüm kullanıcılar için yüklenir; Aksi takdirde, yalnızca geçerli kullanıcı için yüklenir.  
  
  **Bu VSIX yüklü Windows Installer tarafından** onay kutusu  
  Bu onay kutusu seçili değilse, Windows Installer (.msi dosyası); Bu uzantı yüklü Aksi takdirde, tipik VSIX paketi (.vsix dosyası) yüklenir.  
  
  **Varlıklar** sekmesi aşağıdaki denetimleri içerir.  
  
  **Varlıkların listesi**  
  Uzantı veya içerik öğeleri tanımlayan varlık öğeleri listeler bu yüzeyleri paketi. Kaynak, türü ve yol tarafından ayrı ayrı her bir uzantı veya içerik öğesi listelenir. Uzantıları ve içerik öğeleri listesine, değiştirilebilir ve silindi. Bir uzantı veya içerik öğenin yolu ve türünü karşılık gelen `Type` ve `Path` ilişkili öznitelikleri `Asset` öğesi. Aşağıdaki türleri bilinmektedir:  
  
- Microsoft.VisualStudio.Package  
  
- Microsoft.VisualStudio.MefComponent  
  
- Microsoft.VisualStudio.ToolboxControl  
  
- Microsoft.VisualStudio.Samples  
  
- Microsoft.VisualStudio.ProjectTemplate  
  
- Microsoft.VisualStudio.ItemTemplate  
  
- Microsoft.VisualStudio.Assembly  
  
- Microsoft.ExtensionSDK  
  
  Ekleme veya düzenleme bir varlık için varlık mevcut çözümde bir proje veya dosya dosya sistemi ve projenin adı olup olmadığını varlık türünü belirtmeniz gerekir. Katıştırılmış kaydedileceği klasörün adını belirtebilirsiniz.  
  
  Ayrıca, kendi türlerinizi oluşturmak ve bunları benzersiz adlar verin.  
  
  **Bağımlılıkları** sekmesi aşağıdaki denetimleri içerir.  
  
  **Adı, kaynak ve sürüm aralığı**  
  Bu paket, bağlı olduğu diğer paketleri olan bu paket bağımlılık öğelerini listeler. Bir bağımlılık paket belirtilirse, bu paketi yüklemeden önce yüklenmelidir; Aksi takdirde, bu paketi yüklemeniz gerekir.  
  
  Bağımlılık paketlerini tanımlayıcı adı, sürüm aralığı, kaynak ve nasıl çözümlenmesi bağımlılığı olduğunu tarafından belirtilir. Her bağımlılık paket adı, sürümü ve kaynak tarafından ayrı ayrı listelenir. Bağımlılık paketlerini listeye eklenen, değiştirilebilir ve silindi.  
  
  Tanımlayıcı eşleşmelidir `ID` bağımlılık paket meta özniteliği. Kaynak bir proje geçerli çözüme, şu anda yüklü bir uzantı veya bir dosya olabilir. **Nasıl Çözüldü bağımlılığıdır** ayarı, göreli yolun iç içe geçmiş bir paketin veya bağımlılık için indirme konumunu URL'si olabilir. Kimlik, sürüm ve bağımlılık paketinin çözümleme karşılık `Id`, `Version`, ve `Location` ilişkili öznitelikleri `Dependency` öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSIX Uzantı Şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)   
 [Bir VSIX Paketinin Anatomisi](../extensibility/anatomy-of-a-vsix-package.md)

