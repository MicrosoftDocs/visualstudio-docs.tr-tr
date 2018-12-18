---
title: 'Nasıl yapılır: yerleşik yazı tipi ve renk şeması erişim | Microsoft Docs'
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
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6b96cb16182447ca636ee363a2cf62a33dcd6823
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51752935"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Nasıl yapılır: yerleşik yazı tipi ve renk şeması erişim
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio tümleşik geliştirme ortamı (IDE) Düzenleyicisi penceresiyle ilişkilidir yazı tipleri ve renkler bir düzeni vardır. Bu düzen aracılığıyla erişebileceğiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimi.  
  
 Yerleşik yazı tiplerini ve renkleri düzeni kullanmak için bir VSPackage gerekir:  
  
- Varsayılan yazı tipleri ve renkler hizmeti ile kullanmak için bir kategori tanımlayın.  
  
- Kategori varsayılan yazı tipleri ve renkler sunucusuna kaydedin.  
  
- Belirli bir pencere öğeleri yerleşik görüntüleme ve kategoriler kullanarak kullandığını IDE öneri `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` ve `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` arabirimleri.  
  
  IDE penceresi için bir tanıtıcı elde edilen kategoriyi kullanır. Kategori adı görüntülenen **ayarlarını göster:** açılan kutusunda **yazı tipleri ve renkler** özellik sayfası.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Yerleşik yazı tipleri ve renkler kullanarak bir kategori tanımlamak için  
  
1. Rastgele bir GUID oluşturun.  
  
    Bir kategoriyi benzersiz olarak tanımlanabilmesi için kullanılan bu GUID<strong>.</strong> Bu kategori, IDE'nin varsayılan yazı tipleri ve renkler belirtimi kullanır.  
  
   > [!NOTE]
   >  Yazı tipi ve renk verilerle alınırken <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> veya diğer arabirimleri VSPackages yerleşik bilgi başvurmak için bu GUID kullanın.  
  
2. Kategori adı, böylece IDE'de görüntülendiğinde gerektiğinde yerelleştirilebilen VSPackage'nın kaynakları (.rc) dosyasında bir dize tablosu eklenmelidir.  
  
    Daha fazla bilgi için [ekleyerek veya silerek bir dize](http://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Yerleşik yazı tipleri ve renkler kullanarak bir kategori kaydetmek için  
  
1.  Özel bir kategori aşağıdaki konumda kayıt defteri girdisi türü oluşturun:  
  
     [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<Visual Studio sürümü >* \FontAndColors\\*\<Kategori >*]  
  
     *\<Kategori >* kategorisi yerelleştirilmemiş adıdır.  
  
2.  Stok yazı tipi ve renk şeması dört değerlerle kullanılacak kayıt defteri doldurun:  
  
    |Ad|Tür|Veri|Açıklama|  
    |----------|----------|----------|-----------------|  
    |Kategori|REG_SZ|GUID|Stok yazı tipi ve renk düzenini içeren bir kategoriyi tanımlayan rastgele bir GUID.|  
    |Paket|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Bu GUID, varsayılan yazı tipi ve renk yapılandırmaları kullanan tüm VSPackages tarafından kullanılır.|  
    |Nameıd|REG_DWORD|Kimlik|VSPackage'ı bir yerelleştirilebilir kategori adı kaynak kimliği.|  
    |ToolWindowPackage|REG_SZ|GUID|VSPackage'ı uygulama GUID'i <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimi.|  
  
3.  
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Sistem tarafından sağlanan yazı tipleri ve renkler kullanımı başlatmak için  
  
1. Bir örneğini oluşturmak `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` pencerenin uygulama ve başlatma bir parçası olarak arabirimi.  
  
2. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> örneği elde etmek için yöntemi `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` geçerli karşılık gelen arabirimi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> örneği.  
  
3. Çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> iki kez.  
  
   - İle bir kez çağırmanız `VSEDITPROPID_ViewGeneral_ColorCategory`bağımsız değişken olarak.  
  
   - İle bir kez çağırmanız `VSEDITPROPID_ViewGeneral_FontCategory` bağımsız değişken olarak.  
  
     Bu ayarlar ve varsayılan yazı tipleri ve renkler Hizmetleri penceresinin bir özelliği olarak kullanıma sunar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, kullanımını yerleşik yazı tipleri ve renkler başlatır.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazı tipleri ve renkler kullanma](../extensibility/using-fonts-and-colors.md)   
 [Yazı tipi ve metin renklendirmesi için renk bilgilerini alma](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Saklı yazı tipi ve renk ayarlarını erişme](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Yazı Tipi ve Renklere Genel Bakış](../extensibility/font-and-color-overview.md)

