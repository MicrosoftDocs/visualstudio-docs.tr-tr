---
title: Öğeler ekleme yeni öğe Ekle iletişim kutuları | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ca9ae7d9e4f0ffc031d2dc8db3e940c9b844c57e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778559"
---
# <a name="adding-items-to-the-add-new-item-dialog-boxes"></a>Yeni Öğe Ekleme İletişim Kutularına Öğe Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Öğeler ekleme işlemi **Yeni Öğe Ekle** iletişim kutusu, kayıt defteri anahtarları ile başlar. Aşağıdaki kayıt defteri girdilerini gösterildiği gibi AddItemTemplates bölümü içinde kullanılabilir hale hangi öğelerin dizin adını ve yolunu içeren **Yeni Öğe Ekle** iletişim kutusu konur.  
  
> [!NOTE]
>  Hemen kod kesimi aşağıdaki tabloda, kayıt defteri girişi hakkında ek bilgiler içerir.  
  
 Bu bölümde, [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects] altında yer alır.  
  
 Bu tür projeleri için CLSID ilk GUID'dir; İkinci GUID kayıtlı proje türü için Öğe Ekle şablonları gösterir.  
  
 \\{C061DB26-5833-11D2-96F5-000000000000} \AddItemTemplates\TemplateDirs\ {ACEF4EB2-57CF-11D2-96F4-000000000000} \1  
  
 @="#6"  
  
 "TemplatesDir"="\<Visual Studio SDK yükleme yolunu\\\VSIntegration\\\SomeFolder\\\SomePackage\\\SomeProject\\\SomeProjectItems"  
  
 "SortPriority" dword:00000064 =  
  
|Ad|Tür|(.Rgs dosyasındaki) verileri|Açıklama|  
|----------|----------|-----------------------------|-----------------|  
|(Varsayılan) @|REG_SZ|#% IDS_ADDITEM_TEMPLATES_ENTRY %|Kaynak kimliği için **Öğe Ekle** şablonları.|  
|VAL TemplatesDir|REG_SZ|%TEMPLATE_PATH%\ SomeProjectItems|Görüntülenen iletişim kutusu için proje öğelerinin yolu **Yeni Öğe Ekle** Sihirbazı.|  
|VAL SortPriority|REG_DWORD|100 ([!INCLUDE[vcprx64](../../includes/vcprx64-md.md)])|Ağaç düğümünde görüntülenen dosyaların sıralama düzeni belirler **Yeni Öğe Ekle** iletişim kutusu.|  
  
> [!NOTE]
>  Visual C# ve Visual Basic proje türleri GUID'LERİNİ aşağıdaki gibidir:[!INCLUDE[csprcs](../../includes/csprcs-md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}[!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  
  
 Dizin, % TEMPLATE_PATH%\SomeProjectItems olan TemplateDirs sol tarafındaki düğümü için listelenen **Yeni Öğe Ekle** iletişim kutusu ağaç. Ek öğeler ağacında, kök dizin içinde alt dizini temel alır. Dosyalar projeye eklenecek kullanılabilir maddelerinin sağ bölmede **Yeni Öğe Ekle** iletişim kutusu.  
  
 Genellikle, bu klasör bir şablon HTML veya .cpp dosyası gibi projeniz için şablon dosyalarını ve sihirbazları başlatmak için .vsz dosyaları içerir. Öğelerin nasıl görüntüleneceğini denetlemek için dizin adları ve simgeleri yerelleştirme için .vsdir dosyalarını da içerebilir. Yeni Öğe Ekle iletişim kutusu ağacı bu düğümün temsil ettiği iletişim kutusunda görüntülenen açıklamalı alt yazı yerelleştirilmiş dizedir.  
  
 Ancak, her şeyi bir .vsdir dosyasında olması gerekmez. Dizindeki her öğe için bir .vsdir dosyası olabilir. Daha fazla bilgi için [Sihirbazı (. Vsz) dosya](../../extensibility/internals/wizard-dot-vsz-file.md) ve [şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
> [!NOTE]
>  Şablon dizinlerde .vsdir dosyalarını isteğe bağlıdır. Yalnızca görüntüleyin ve bir proje öğesi koymak istiyorsanız **Yeni Öğe Ekle** iletişim kutusu, TemplatesDir deyiminde belirtilen şablonları dizininde bu dosyayı koyabilir. Dosyayı daha sonra sağ bölmede görüntülenir **Yeni Öğe Ekle** iletişim kutusu için proje. Ancak, yerelleştirilmiş bir açıklamalı alt yazı dosyası veya bir simge görüntülemek istiyorsanız, şablonları dizinde .vsdir en az bir dosya içermelidir.  
  
## <a name="grouping-project-items"></a>Proje öğeleri gruplandırma  
 Şablon grupları klasörlerdeki içermesini istiyorsanız **Yeni Öğe Ekle** iletişim kutusu ağacında, bunları öğelerle şablon dizin alt dizinler olması gerekir. Zaman **Yeni Öğe Ekle** kullanıcılara iletişim kutusu görüntülenir, bunlar ayrıca alt klasörleri görebilir ve bunları proje öğelerini seçebilirsiniz.  
  
 Bu şablon dizin ağacında uzlu stromu diğer öğeleri göre oluşturulacağı kod kesimi sıralama öncelik belirler. İçin **Yeni Öğe Ekle** iletişim kutusu, sıralama önceliği olan eklemeniz gerekir ve böylece öğelerinizi doğru konumda iletişim kutusunda görüntülenen tüm.  
  
 Ayrıca uygulayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> ne görüntülenen filtrelemek için arabirimi **Yeni Öğe Ekle** iletişim kutusu. Bu arabirimi uygulayan bir şablon dizini 50 şablonu ve sihirbaz dosyaları içerir, örneğin, diskte ayarlayabilirsiniz. Bu şekilde, bir proje türü, proje başka bir türe ait bir 30 dosyaları ve genel türde bir proje içinde kullanılabilir olan tüm dosyaları ait 20 dosyaları farklı proje türlerine sahip olabilir. Bağlı olarak hangi proje şablonu oluşturulur, bu şekilde, farklı bir şablon dosyaları kümesini görüntüleyebilirsiniz.  
  
 Örneğin, bir Visual Basic projesinde, Web projeleri ve istemci projeler olabilir. Web formları için bir istemci projesi eklemek için kullanışlı öğeleri değildir ve windows forms bir Web sunucusu projeye eklemek için kullanışlı öğeleri değildir. Bu nedenle, her iki türde bir proje için tüm dosyaları içeren bir şablon dizin oluşturabilirsiniz. Ardından uygulayarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, proje veya proje ayarlarını proje türüne göre değil görüntülenmesi gereken öğeleri gizleyebilirsiniz.  
  
## <a name="filtering-project-items"></a>Proje öğeleri filtreleme  
 `IVsFilterAddProjectItemDlg2` öğe ağacında (sol bölmede) ve proje dosyaları (sağ bölme) aşağıdaki yollarla filtreleme için sağlar:  
  
- Yerelleştirilmiş adlarıyla (.vsdir dosyada bulunan iletişim kutusunda görüntülenen açıklamalı alt yazılar) tarafından sağlanan `IVsFilterAddProjectItemDlg`.  
  
- Dosya ve klasörleri diskte gerçek adlarını tarafından (yerelleştirilmemiş — .vsdir dosya) tarafından sağlanan `IVsFilterAddProjectItemDlg`.  
  
- Tarafından sağlanan kategoriye `IVsFilterAddProjectItemDlg2`.  
  
  Kategoriye göre filtrelemek için bir "Web formu" gibi .vsdir dosyasındaki öğenin veya "İstemci öğesi" Visual Basic'te bir kategori dize sağlayın. İletişim kutusu kodu kategori sınıflandırma .vsdir dosyasından alır ve size geçirir. Uygulamanız için bu bilgileri geçirebilirsiniz `IVsFilterAddProjectItemDlg2` filtrelemek için **Yeni Öğe Ekle** kategorilere göre iletişim kutusu. Ayrıca, Web sayfaları veya istemci Win32 uygulama çalışmaları olarak öğeleri filtreleyebilirsiniz. Ayrıca, tanımlayabilirsiniz [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] öğeleri Microsoft Foundation Classes (MFC) veya Etkin Şablon kitaplığı (ATL) öğeleri olarak etiketlenir. Bu öğeleri tespit ederken, proje sistemi sistem kategorilerini ve sınıflandırmalarını göre filtrelenebilir. böylece kendi sınıflandırmaları tanımlayabilirsiniz.  
  
  Bu filtre işlevi uygularsanız, gizlenmelidir her öğenin bir tablo eşleme gerekmez. Yalnızca, tür olarak öğeleri sınıflandırmak ve .vsdir dosya veya dosyalar sınıflandırmalar yerleştirin. Ardından arabirimi uygulanarak belirli bir sınıflandırma olan öğelerden biri gizleyebilirsiniz. Bu şekilde, öğeleri yapabileceğiniz **Yeni Öğe Ekle** iletişim kutusu dinamik tabanlı proje içindeki durumu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projeleri için genellikle kullanılan nesnelerin Catıdlerini](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Şablon dizin açıklaması (. Vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Sihirbaz (.Vsz) Dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)

