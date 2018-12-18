---
title: Öğeler ekleme yeni öğe Ekle iletişim kutuları | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, adding items
ms.assetid: 2f70863b-425b-4e65-86b4-d6a898e29dc7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b98e696def519cea6d3644d0ef3a48bc82c19136
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49812588"
---
# <a name="add-items-to-the-add-new-item-dialog-box"></a>Yeni Öğe Ekle iletişim kutusu öğeleri Ekle
Öğeler ekleme işlemi **Yeni Öğe Ekle** iletişim kutusu, kayıt defteri anahtarları ile başlar. Aşağıdaki kayıt defteri girdilerini gösterildiği gibi **AddItemTemplates** bölüm içeren yolu ve adı dizinde bulunan yapılan hangi öğelerin **Yeni Öğe Ekle** iletişim kutusu konur.  

> [!NOTE]
>  Hemen kod kesimi aşağıdaki tabloda, kayıt defteri girişi hakkında ek bilgiler içerir.  

 Bu bölümde altında bulunan **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0Exp\Projects**.

 Bu tür projeleri için CLSID ilk GUID'dir; İkinci GUID Öğe Ekle şablonları için kayıtlı bir proje türü gösterir:  

 **\\{C061DB26-5833-11D2-96F5-000000000000} \\AddItemTemplates\\TemplatesDir\\{ACEF4EB2-57CF-11D2-96F4-000000000000}\\1**

 **@** #6 = 

 **TemplatesDir** = \\&lt;Visual Studio SDK yükleme yolunu&gt;\\VSIntegration\\&lt;SomeFolder&gt; \\ &lt;SomePackage&gt;\\&lt;SomeProject&gt;\\&lt;SomeProjectItems&gt;

 **SortPriority** dword:00000064 =


| Ad | Tür | Veri (gelen *.rgs* dosya) | Açıklama |
|------------------|-----------| - | - |
| (Varsayılan) @ | REG_SZ | #% IDS_ADDITEM_TEMPLATES_ENTRY % | Kaynak kimliği için **Öğe Ekle** şablonları. |
| VAL TemplatesDir | REG_SZ | TEMPLATE_PATH %\\&lt;SomeProjectItems&gt; | Görüntülenen iletişim kutusu için proje öğelerinin yolu **Yeni Öğe Ekle** Sihirbazı. |
| VAL SortPriority | REG_DWORD | 100 ([!INCLUDE[vcprx64](../../extensibility/internals/includes/vcprx64_md.md)]) | Ağaç düğümünde görüntülenen dosyaların sıralama düzeni belirler **Yeni Öğe Ekle** iletişim kutusu. |

> [!NOTE]
>  Visual C# ve Visual Basic proje türleri GUID'LERİNİ aşağıdaki gibidir: 
> - [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]: {FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}
> - [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]: {F184B08F-C81C-45F6-A57F-5ABD9991F28F}  

 Listelenen directory **TemplatesDir**, olduğu *TEMPLATE_PATH %\\&lt;SomeProjectItems&gt;*, düğüm sol tarafındaki **Ekle Yeni öğe** iletişim kutusu ağaç. Ek öğeler ağacında, kök dizin içinde alt dizini temel alır. Dosyalar projeye eklenecek kullanılabilir maddelerinin sağ bölmede **Yeni Öğe Ekle** iletişim kutusu.  

 Genellikle, bu klasör gibi bir şablon HTML projeniz için şablon dosyalarını içerecek veya *.cpp* dosyasını ve tüm *.vsz* sihirbazları başlatmak için dosyaları. Öğelerin nasıl görüntüleneceğini denetlemenizi de ekleyebilirsiniz *.vsdir* dizin adları ve simgeleri yerelleştirme dosyaları. Yerelleştirilmiş dize arar: Bu düğümde temsil eden iletişim kutusunda görüntülenen başlıktır **Yeni Öğe Ekle** iletişim kutusu ağaç.  

 Ancak, her şeyi birinde olması gerekmez *.vsdir* dosya. Bir sahip *.vsdir* dizindeki her öğe için dosya. Daha fazla bilgi için [sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md) ve [şablon dizin açıklaması (.vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  

> [!NOTE]
>  *.Vsdir* şablon dizinlerde dosyaları isteğe bağlı. Yalnızca görüntüleyin ve bir proje öğesi koymak istiyorsanız **Yeni Öğe Ekle** iletişim kutusu, belirtilen şablonları dizininde bu dosyayı koyabilir **TemplatesDir** deyimi. Dosyayı daha sonra sağ bölmede görüntülenir **Yeni Öğe Ekle** iletişim kutusu için proje. Yerelleştirilmiş bir açıklamalı alt yazı dosyası veya bir simge görüntülemek istiyorsanız, ancak en az bir tane eklemeniz gerekir *.vsdir* şablonları dizinde dosya.  

## <a name="group-project-items"></a>Proje öğeleri gruplandırma  
 Şablon grupları klasörlerdeki içermesini istiyorsanız **Yeni Öğe Ekle** iletişim kutusu ağacında, bunları öğelerle şablon dizin alt dizinler olması gerekir. Zaman **Yeni Öğe Ekle** kullanıcılara iletişim kutusu görüntülenir, bunlar ayrıca alt klasörleri görebilir ve bunları proje öğelerini seçebilirsiniz.  

 Bu şablon dizin ağacında uzlu stromu diğer öğeleri göre oluşturulacağı kod kesimi sıralama öncelik belirler. İçin **Yeni Öğe Ekle** iletişim kutusu, sıralama önceliği olan eklemeniz gerekir ve böylece öğelerinizi doğru konumda iletişim kutusunda görüntülenen tüm.  

 Ayrıca uygulayabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> ne görüntülenen filtrelemek için arabirimi **Yeni Öğe Ekle** iletişim kutusu. Bu arabirimi uygulayan bir şablon dizini 50 şablonu ve sihirbaz dosyaları içerir, örneğin, diskte ayarlayabilirsiniz. Bu şekilde, bir proje türü, proje başka bir türe ait bir 30 dosyaları ve genel türde bir proje içinde kullanılabilir olan tüm dosyaları ait 20 dosyaları farklı proje türlerine sahip olabilir. Bağlı olarak hangi proje şablonu oluşturulur, bu şekilde, farklı bir şablon dosyaları kümesini görüntüleyebilirsiniz.  

 Örneğin, bir Visual Basic projesinde, Web projeleri ve istemci projeler olabilir. Web formları için bir istemci projesi eklemek için kullanışlı öğeleri değildir ve windows forms bir Web sunucusu projeye eklemek için kullanışlı öğeleri değildir. Bu nedenle, her iki türde bir proje için tüm dosyaları içeren bir şablon dizin oluşturabilirsiniz. Ardından, uygulama tarafından <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>, proje veya proje ayarlarını proje türüne göre değil görüntülenmesi gereken öğeleri gizleyebilirsiniz.  

## <a name="filter-project-items"></a>Proje öğeleri Filtrele  
 `IVsFilterAddProjectItemDlg2` öğe ağacında (sol bölmede) ve proje dosyaları (sağ bölme) aşağıdaki yollarla filtreleme için sağlar:  

- Yerelleştirilmiş adlarına göre (bulunan iletişim kutusunda görüntülenen açıklamalı alt yazılar *.vsdir* dosya) tarafından sağlanan `IVsFilterAddProjectItemDlg`.  

- Dosya ve klasörleri diskte gerçek adlarını tarafından (yerelleştirilmemiş — hiçbir *.vsdir* dosya) tarafından sağlanan `IVsFilterAddProjectItemDlg`.  

- Tarafından sağlanan kategoriye `IVsFilterAddProjectItemDlg2`.  

  Kategoriye göre filtrelemek için bir kategori dize içindeki bir öğeyi sağlamak *.vsdir* gibi dosya *Web formu* veya *istemci öğesi* Visual Basic'te. İletişim kutusu kodu sonra kategori sınıflandırma alır *.vsdir* dosya ve size geçirir. Uygulamanız için bu bilgileri geçirebilirsiniz `IVsFilterAddProjectItemDlg2` filtrelemek için **Yeni Öğe Ekle** kategorilere göre iletişim kutusu. Ayrıca, Web sayfaları veya istemci Win32 uygulama çalışmaları olarak öğeleri filtreleyebilirsiniz. Ayrıca, tanımlayabilirsiniz [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] öğeleri Microsoft Foundation Classes (MFC) veya Etkin Şablon kitaplığı (ATL) öğeleri olarak etiketlenir. Bu öğeleri tespit ederken, proje sistemi sistem kategorilerini ve sınıflandırmalarını göre filtrelenebilir. böylece kendi sınıflandırmaları tanımlayabilirsiniz.  

  Bu filtre işlevi uygularsanız, gizlenmelidir her öğenin bir tablo eşleme gerekmez. Yalnızca öğe türlerine sınıflandırmak ve sınıflandırmaları koymak *.vsdir* dosya veya dosyalar. Ardından arabirimi uygulanarak belirli bir sınıflandırma olan öğelerden biri gizleyebilirsiniz. Bu şekilde, öğeleri yapabileceğiniz **Yeni Öğe Ekle** iletişim kutusu dinamik tabanlı proje içindeki durumu.  

## <a name="see-also"></a>Ayrıca bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Proje ve öğe şablonlarını kaydetme](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Projeleri için genellikle kullanılan nesnelerin Catıdlerini](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)   
 [Proje ve proje öğesi şablonları ekleme](../../extensibility/internals/adding-project-and-project-item-templates.md)   
 [Şablon dizin açıklaması (.vsdir) dosyaları](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)   
 [Sihirbaz (.vsz) dosyası](../../extensibility/internals/wizard-dot-vsz-file.md)