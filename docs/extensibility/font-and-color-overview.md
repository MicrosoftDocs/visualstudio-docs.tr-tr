---
title: Yazı tipi ve renk genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], font and color
- font and color control [Visual Studio SDK], editors
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: adf5877ae9b01666491e5d10522ba52b58b2d917
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845231"
---
# <a name="font-and-color-overview"></a>Yazı tipi ve renk genel bakış
Bu konuda ele alınmıştır metin yazı tipi ve renk ayarlarını [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE). Kategorileri ve öğeleri görüntüleme kavramlarını da tanıtılmaktadır ve VSPackages ve çekirdek düzenleyici metin özniteliklerini kullanma açıklanmaktadır.  
  
## <a name="the-fonts-and-colors-property-page"></a>Yazı tipleri ve renkler özellik sayfası  
 Görüntülenen metin özniteliklerini yönetebilir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamı (IDE) üzerinden **yazı tipleri ve renkler** özellik sayfası. Bulunacak **yazı tipleri ve renkler** özellik sayfasında **Araçları** menüsünde tıklayın **seçenekleri**. Genişletin **ortam**ve ardından **yazı tipleri ve renkler**.  
  
## <a name="categories-and-display-items"></a>Kategorileri ve öğeleri görüntüleme  
 Yazı tipleri ve renkler halinde düzenlenir **kategorileri** ve **görünen öğeler**.  
  
- A **kategori** bir dizi için mantıksal ya da işlevsel bir kapsayıcı **görünen öğeler**.  
  
   Listesini **kategorileri** bulunduğu **ayarlarını göster** açılan kutusunda **yazı tipleri ve renkler** özellik sayfası.  
  
- A **görüntü öğesi** yorum, bir dize veya görüntülendiğinde renklendirilmiş için bir denetim yapısı gibi iyi tanımlanmış metin varlıktır.  
  
  Her **görüntü öğesi** içinde benzersiz şekilde tanımlanan **kategori** , içerir. Sonuç olarak, birden fazla **kategori** olabilir bir **görüntü öğesi** aynı ada sahip.  
  
## <a name="vspackage-control-of-fonts-and-colors"></a>VSPackage'ı denetimin yazı tipleri ve renkler  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] Vspackages'a sağlar:  
  
- Yazı tipi ve renk tanımla **kategorileri**.  
  
- Yazı tipleri ve renkler sunmak için kullanılan belirtin **görünen öğeler**.  
  
- Etkileşim **yazı tipleri ve renkler** özellik sayfası.  
  
- Toplama birden çok **kategorileri** gruplar.  
  
- Varsayılan ayarlarında değişiklikler kalıcı hale getirin.  
  
  İçindeki yazı tipini ve rengini seçimleri ile etkileşim kurmak için iki yolla [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
- Tek yönlü olarak adlandırılır *söz dizimi renklerini*. Varolan özelleştiren VSPackage tarafından kullanılan [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dil hizmeti uygulamak ve bir kaynak düzenleyici oluşturmak için düzenleyici.  
  
   Yalnızca bir **kategori** Bu mekanizma, yani destekler, **metin düzenleyici**.  
  
- Diğer tüm daha genel bir alternatif destekler **kategorileri** ve kullanıcı arabirimi bileşenleri metin görüntülenirken Kaynak Düzenleyicisi dışında. Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## <a name="core-editor-text-settings"></a>Çekirdek düzenleyici metin ayarları  
 Dil hizmeti nesnesinin çekirdek Düzenleyici yazı tipi ve renk ayarlarını tabidir **metin EditorCategory** bulunan **ayarlarını göster** açılan kutusunda **yazı tipleri ve renkler** özellik sayfası.  
  
 Düzenleyicilerle çalışırken, özel yazı tipi ve denetlemek ve genişletmek için dil hizmeti sunan renkli denetimi mekanizmasını kullanmalısınız **metin düzenleyici** ayarları. Mekanizması olarak adlandırılır *söz dizimi renklendirmesi* sağlar:  
  
- Yazı tipleri ve renkler görüntü öğeleri yönetmek için basitleştirilmiş bir tekniktir.  
  
   Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
- İyi tanımlanmış ve en iyi duruma getirilmiş renklendirme mekanizması.  
  
   Daha fazla bilgi için bkz. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
- Her iki özelliği kullanmak yerleşik görüntü öğeleri **metin EditorCategory** ve bunları genişletmek için.  
  
   Daha fazla bilgi için [nasıl yapılır: yerleşik renklendirilebilir öğeleri kullanma](../extensibility/internals/how-to-use-built-in-colorable-items.md) ve [özel renklendirilebilir öğeler](../extensibility/internals/custom-colorable-items.md).  
  
- Otomatik Kalıcılık geçerli durumu hem yerleşik ve özel görüntü öğeleri ile **metin düzenleyici** kategorisi.  
  
  Bkz: renklendirme söz dizimi hakkında daha fazla bilgi için [eski dil hizmetinde söz dizimi renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Eski arabirimleri Düzenleyicisi](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Eski dil hizmetinde söz dizimi renklendirmesi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)