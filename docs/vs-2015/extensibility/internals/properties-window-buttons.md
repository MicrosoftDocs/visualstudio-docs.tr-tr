---
title: Özellikler penceresi düğmeleri | Microsoft Docs
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
- Properties window, buttons
ms.assetid: bdd2e3a7-ae6e-4e88-be1a-e0e3b7ddbbcc
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bb6a3802e135c02b4ccc7b27aca69b2afd2a9f70
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51789856"
---
# <a name="properties-window-buttons"></a>Özellikler Penceresi Düğmeleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir geliştirme dilini ve ürün türüne bağlı olarak, belirli düğmelere varsayılan araç çubuğunda görüntülenen **özellikleri** penceresi. Tüm durumlarda **kategorilere göre**, **Alphabetized**, **özellikleri**, ve **özellik sayfaları** düğmeleri görüntülenir. Visual C# ve Visual Basic **olayları** düğmesi de görüntülenir. Belirli Visual C++ projelerinde **VC ++ iletileri** ve **VC geçersiz kılmalar** düğmeleri görüntülenir. Ek düğmeler, diğer proje türleri için görüntülenebilir. Düğmeler hakkında daha fazla bilgi için **özellikleri** penceresinde görmek [Özellikler penceresi](../../ide/reference/properties-window.md).  
  
## <a name="implementation-of-properties-window-buttons"></a>Özellikler penceresi düğmeleri uygulaması  
 Tıkladığınızda **kategorilere göre** button, Visual Studio çağrıları <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> arabirimi özelliklerini kategoriye göre sıralamak için odağa sahip nesne. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties> üzerinde uygulanan `IDispatch` sunulan nesne **özellikleri** penceresi.  
  
 Negatif değerlere sahip 11 önceden tanımlanmış bir özellik kategorisi vardır. Özel kategoriler tanımlayabilirsiniz, ancak bunları önceden tanımlanmış kategorilerden bunları ayırt etmek için pozitif değerlere atamanızı öneririz.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.MapPropertyToCategory%2A> Yöntemi, belirtilen özellik için uygun özellik kategorisi değeri döndürür. <xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties.GetCategoryName%2A> Yöntemi kategori adı içeren bir dize döndürür. Visual Studio standart özellik kategorisi değerleri bildiğinden özel kategori değerleri için destek sağlamak yeterlidir.  
  
 Tıkladığınızda **Alphabetized** düğmesi, özellikleri alfabetik olarak ada göre görüntülenir. Adları tarafından alınır `IDispatch` yerelleştirilmiş Sıralama algoritması göre.  
  
 Zaman **özellikleri** penceresi açıkken, **özellikleri** düğmesi otomatik olarak gösterilen seçili. Ortamın diğer bölümlerinde aynı düğmesi görüntülenir ve göstermek için tıklayın **özellikleri** penceresi.  
  
 **Özellik sayfaları** düğmesi kullanılamıyorsa, `ISpecifyPropertyPages` seçili nesne için uygulanmadı. Çözüm ve projelerle ilişkili görüntü yapılandırma bağımlı özellikleri özellik sayfaları, ancak bunlar olması da olabilir (örneğin, Visual C++'ta) proje öğeleri ile ilişkili.  
  
> [!NOTE]
>  Araç çubuğu düğmelerine ekleme yapamazsınız **özellikleri** yönetilmeyen kod kullanarak pencere. Araç çubuğu düğmesi eklemek için türetilen bir yönetilen nesne oluşturma <xref:System.Windows.Forms.Design.PropertyTab>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)

