---
title: Özellikler penceresi alanları ve arabirimleri | Microsoft Docs
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
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8b9e7705af131bdc8c81b6cbeeac3ed4dda80aa4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721029"
---
# <a name="properties-window-fields-and-interfaces"></a>Özellikler Penceresi Alanları ve Arabirimleri
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Seçim, hangi bilgilerin görüntüleneceğini belirlemek modelin **özellikleri** penceresi odaklı IDE'de pencerenin temel alır. Her pencere ve seçili penceresi içinde nesne genel seçimi bağlamına gönderildi, Seçim bağlam nesnesi olabilir. Bu pencere odaklandığında ortamı genel seçim bağlamını pencere çerçevesi değerlerini güncelleştirir. Bu nedenle odağı değiştiğinde seçim bağlamını yapar.  
  
## <a name="tracking-selection-in-the-ide"></a>IDE'de seçim izleme  
 Pencere çerçevesi veya site, IDE tarafından sahip olunan adlı bir hizmet olan <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Bir değişiklik nasıl bir kullanıcı başka bir açık penceresine odak değiştirme ya da farklı proje öğesinde seçerek kaynaklanan bir seçimi aşağıdaki adımları Göster **Çözüm Gezgini**, içindegörüntüleneniçerikdeğiştirmekiçinuygulanır **Özellikleri** penceresi.  
  
1. Seçilen pencere çağrılarında tarihli VSPackage'ı tarafından oluşturulan nesne <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> olmasını <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> çağırma <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2. Seçilen pencere tarafından sağlanan seçim kapsayıcısı kendi oluşturur <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesne. Seçim değişiklikleri VSPackage çağırdığında <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ortamında, tüm dinleyici bildirmek için de dahil olmak üzere **özellikleri** pencerenin Değiştir. Ayrıca, yeni seçime ilgili hiyerarşi ve öğe bilgilerine erişim sağlar.  
  
3. Çağırma <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> ve Seçili hiyerarşiyi öğeleri geçirerek `VSHPROPID_BrowseObject` parametresi doldurur <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesne.  
  
4. Türetilen bir nesne [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) için döndürülen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> İstenen öğe ve ortam içine sarmalar bir <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (bkz. aşağıdaki adım). Çağrı başarısız olursa ortam ikinci çağrıda `IVsHierarchy::GetProperty`, seçim kapsayıcısı geçirme <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> hiyerarşi öğesi veya öğelerini sağlayın.  
  
    VSPackage oluşturmaz, projenizi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ortamı tarafından sağlanan penceresi VSPackage, onu uyguladığından (örneğin, **Çözüm Gezgini**) yapıları <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> kendi adına.  
  
5. Ortam yöntemlerini çağırır <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nesneleri göre almak için `IDispatch` doldurun için arabirim **özellikleri** penceresi.  
  
   Bir değer olduğunda **özellikleri** penceresi değiştirildiğinde, VSPackages uygulamak `IVsTrackSelectionEx::OnElementValueChangeEx` ve `IVsTrackSelectionEx::OnSelectionChangeEx` değişikliği için öğe değeri bildirmek için. Ardından ortamın çağırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> veya <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> görüntülenen bilgileri tutmak **özellikleri** pencereyi eşzamanlı özellik değerleri. Daha fazla bilgi için [Özellikler penceresindeki özellik değerlerini güncelleştirme](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Farklı bir seçmenin yanı sıra içinde proje öğesi **Çözüm Gezgini** öğeyle ilişkili özellikleri görüntülemek için de kullanılabilir aşağı açılan listeyi kullanarak bir form veya belge penceresi içinde farklı bir nesne seçebilirsiniz **Özellikleri** penceresi. Daha fazla bilgi için [Özellikler penceresi nesne listesi](../../extensibility/internals/properties-window-object-list.md).  
  
   Bilgi görüntülendiği şekilde değiştirebilirsiniz **özellikleri** penceresi kılavuzdan alfabetik kategorik için ve kullanılabilir olması durumunda da seçilen bir nesne için bir özellik sayfası üzerindeuygundüğmeleretıklayarakaçabilirsiniz **Özellikleri** penceresi. Daha fazla bilgi için [Özellikler penceresi düğmeleri](../../extensibility/internals/properties-window-buttons.md) ve [özellik sayfaları](../../extensibility/internals/property-pages.md).  
  
   Son olarak, listenin sonuna **özellikleri** penceresinde de seçilen alanın açıklaması bulunur **özellikleri** pencere kılavuzunun. Daha fazla bilgi için [alma alan açıklamaları Özellikler penceresinden](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Özellikleri Genişletme](../../extensibility/internals/extending-properties.md)

