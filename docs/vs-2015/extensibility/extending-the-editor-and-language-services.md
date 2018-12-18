---
title: Düzenleyici ve dil hizmetlerini genişletme | Microsoft Docs
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
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 91eab151680d936c350c8c5745aec6c9fe86e47c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723062"
---
# <a name="extending-the-editor-and-language-services"></a>Düzenleyiciyi ve Dil Hizmetlerini Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kendi düzenleyicinizi için dil hizmeti özellikleri (örneğin, IntelliSense) ekleyin ve özelliklerin çoğunu Visual Studio Kod Düzenleyicisi'ni genişletin.  Genişletebilirsiniz tam listesi için bkz. [dil hizmeti ve düzenleyici uzantı noktaları](../extensibility/language-service-and-editor-extension-points.md).  
  
 Çoğu Düzenleyici özellikleri, Yönetilen Genişletilebilirlik Çerçevesi (MEF) kullanarak genişletin. Örneğin, söz dizimi renklendirme, genişletmek istediğiniz Düzenleyici özelliği ise, bir MEF yazabilirsiniz *bileşen parçası* istediğiniz farklı renklendirme ve bunları ele istediğiniz nasıl sınıflandırmalarını tanımlar. Düzenleyici, aynı özellik birden fazla uzantı da destekler.  
  
 Düzenleyici sunu katmanını temel Windows Presentation Framework (WPF). WPF Grafik kitaplığı için esnek metin biçimlendirme sağlar ve ayrıca grafik ve animasyon gibi görsel öğeler sağlar.  
  
 Visual Studio SDK'sı olarak da bilinen bağdaştırıcıları sağlar *dolgular* önceki sürümleri için yazılmış VSPackages desteklemek için. Bununla birlikte, mevcut bir VSPackage varsa, daha iyi performans ve güvenilirlik elde etmek için yeni teknoloji güncelleştirme öneririz.  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Dil Hizmeti ve Düzenleyici Uzantılarıyla Çalışmaya Başlama](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Düzenleyici uzantısı oluşturma açıklanır.|  
|[Düzenleyicinin İçinde](../extensibility/inside-the-editor.md)|Düzenleyici genel yapısını açıklar ve bazı özellikleri listeler.|  
|[Düzenleyicide Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)|Yönetilen Genişletilebilirlik Çerçevesi (MEF) düzenleyiciyle kullanmayı açıklar.|  
|[Dil Hizmeti ve Düzenleyici Uzantı Noktaları](../extensibility/language-service-and-editor-extension-points.md)|Düzenleyici uzantı noktaları listeler. Uzantı noktaları Genişletilebilir Düzenleyici özelliklerini temsil eder.|  
|[İzlenecek Yol: Görünüm Kenarlığı, Komutlar ve Ayarlar (Sütun Kılavuzları) Oluşturma](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Size yol gösterir ve belirli bir ekran genişliği kod sağlamanıza yardımcı olmak için sütun gudie satırları çizen bir görünüm kenarlığı oluşturma açıklanmaktadır.  Ayrıca, okuma ve yazma ayarları yanı sıra bildirme ve komut penceresinden çağırabilirsiniz komutlar uygulama gösterir.|  
|[Düzenleyici İçeri Aktarımları](../extensibility/editor-imports.md)|Bir uzantı aktarabilirsiniz hizmetler listelenir.|  
|[Eski Kodu Düzenleyiciye Uyarlama](../extensibility/adapting-legacy-code-to-the-editor.md)|Eski kod (önceden Visual Studio Düzenleyicisi'ni genişletmek için 2010) uyarlamak için farklı yollar açıklanmaktadır.|  
|[Eski Dil Hizmetini Geçirme](../extensibility/internals/migrating-a-legacy-language-service.md)|VSPackage'ı temel dil hizmetini geçirme açıklanmaktadır.|  
|[İzlenecek Yol: Bir İçerik Türünü Dosya Adı Uzantısına Bağlama](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Bir içerik türü için bir dosya adı uzantısına bağlama işlemi gösterilmektedir.|  
|[İzlenecek Yol: Dış Boşluk Karakteri Oluşturma](../extensibility/walkthrough-creating-a-margin-glyph.md)|Simge kenar boşluğuna ekleme işlemi gösterilmektedir.|  
|[İzlenecek Yol: Metni Vurgulama](../extensibility/walkthrough-highlighting-text.md)|Nasıl kullanılacağını gösterir *etiketleri* metni vurgulayın.|  
|[İzlenecek Yol: Ana Hat Oluşturma](../extensibility/walkthrough-outlining.md)|Küme ayraçları belirli bir tür için anahat oluşturma ekleme işlemi gösterilmektedir.|  
|[İzlenecek Yol: Eşleşen Küme Ayraçlarını Görüntüleme](../extensibility/walkthrough-displaying-matching-braces.md)|Eşleşen küme ayraçlarını vurgulamak gösterilmektedir.|  
|[İzlenecek Yol: HızlıBilgi Araç İpuçlarını Görüntüleme](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Özellikler, yöntemler ve olaylar gibi kod öğeleri açıklayan Hızlıbilgi açılan pencereler görüntüleme işlemini göstermektedir.|  
|[İzlenecek Yol: İmza Yardımını Görüntüleme](../extensibility/walkthrough-displaying-signature-help.md)|Bir imzada sayısı ve parametre türleri hakkında bilgiler vermemiz açılan pencereler görüntüleme işlemini göstermektedir.|  
|[İzlenecek Yol: Deyim Tamamlamayı Görüntüleme](../extensibility/walkthrough-displaying-statement-completion.md)|Deyim tamamlama uygulanması gösterilmektedir.|  
|[İzlenecek Yol: Kod Parçacıkları Uygulama](../extensibility/walkthrough-implementing-code-snippets.md)|Kod parçacığı genişletme uygulanması gösterilmektedir.|  
|[İzlenecek Yol: Ampul Önerilerini Görüntüleme](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Ampuller kod öneriler için görüntüleme işlemini göstermektedir.|  
|[İzlenecek Yol: Düzenleyici Uzantısı ile Kabuk Komutu Kullanma](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Bir menü komutu vspackage'ta bir MEF Bileşeni ile ilişkilendirilecek gösterilmektedir.|  
|[İzlenecek Yol: Düzenleyici Uzantısı ile Kısayol Tuşu Kullanma](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Bir MEF Bileşeni ile menü kısayolu vspackage'ta ilişkilendirilecek gösterilmektedir.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Bilgi hakkında Yönetilen Genişletilebilirlik Çerçevesi (MEF) sağlar.|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Windows Presentation Foundation (WPF) hakkında bilgi sağlar.|  
  
## <a name="reference"></a>Başvuru  
 Visual Studio düzenleyicisinde, aşağıdaki ad alanlarını içerir.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities>

