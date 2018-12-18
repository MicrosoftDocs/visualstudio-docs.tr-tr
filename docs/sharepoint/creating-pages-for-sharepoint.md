---
title: SharePoint için sayfa oluşturma | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, master pages
- SharePoint development in Visual Studio, page layouts
- SharePoint development in Visual Studio, content pages
- master pages[SharePoint development in Visual Studio], designing
- content pages[SharePoint development in Visual Studio], designing
- page layouts[SharePoint development in Visual Studio], designing
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: ecdbde69735f548b7ab70da132e9e2cc2080bbcb
ms.sourcegitcommit: e6b13898cfbd89449f786c2e8f3e3e7377afcf25
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/22/2018
ms.locfileid: "36326056"
---
# <a name="create-pages-for-sharepoint"></a>SharePoint için sayfa oluşturma
  Uygulama sayfaları, site sayfaları, ana sayfalar ve sayfa düzenleri bir SharePoint sitesinin oluşturabilirsiniz.  
  
 Visual Studio'da bir şablon kullanarak uygulama sayfaları oluşturabilirsiniz. Site sayfaları, ana sayfalar ve sayfa düzenleri, SharePoint Designer kullanarak oluşturun. Ardından, bu sayfaları bir SharePoint Proje ile kullanmak için Visual Studio içe aktarabilirsiniz.  
  
 Görünümü ve davranışı sayfaların geçişli stil sayfaları, ECMAScript ve Temalar kullanarak da değiştirebilirsiniz.  
  
## <a name="types-of-sharepoint-pages"></a>SharePoint sayfaları türleri
 Aşağıdaki tabloda bir SharePoint sitesi içeren sayfaları dört ana türleri açıklanmaktadır.  
  
|Sayfa türü|Açıklama|  
|---------------|-----------------|  
|Uygulama sayfaları|Özel kod içeren sayfasında istediğiniz veya birden çok sitede paylaşılacak sayfa istiyorsanız uygulama sayfası oluşturma. Aksi halde, bir site sayfası en iyi seçim olabilir.|  
|Site sayfaları|Aşağıdaki görevleri gerçekleştirmek istiyorsanız, bir site sayfası oluşturun:<br /><br /> -Sayfaya bir SharePoint kitaplığına ekleyin.<br />-Dinamik Web Bölümleri ve Web Bölümü bölgeleri gibi ana bilgisayar özellikleri sayfasına etkinleştirin.<br />-SharePoint Designer kullanarak sayfayı özelleştirmek kullanıcıların etkinleştirin.<br /><br /> Özel kod içeren sayfasına istiyorsanız, bir site sayfası oluşturmayın. Bir site sayfasına özel kod eklemesi mümkün olsa da, kodu kullanıcı SharePoint Designer kullanarak sayfa özelleştirir zaman çalışmayı durdurur.|  
|Ana sayfalar|Site sayfaları için ortak bir yapıya tanımlamak istiyorsanız bir ana sayfa ve uygulama sayfaları oluşturun.|  
|Sayfa düzenleri|Sayfa düzenleri özgü [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] ve daha fazla site sayfaları ve uygulama sayfaları için ortak bir yapıya tanımlamanıza olanak sağlar.|  
  
 Her tür sayfa genel bakış için bkz: [yapı taşı: sayfaları ve kullanıcı arabirimi](http://go.microsoft.com/fwlink/?LinkID=182095), ve [sayfa düzenleri ve ana sayfalar](http://go.microsoft.com/fwlink/?LinkID=182096).  
  
## <a name="create-application-pages"></a>Uygulama sayfaları oluşturma
 Visual Studio'da Uygulama sayfaları ekleyerek oluşturabilirsiniz bir **uygulama sayfası** bir SharePoint proje öğesi. Sayfasına denetimler ekleme ve ardından kod ekleyerek denetim olayları işlemek.  
  
 Sayfa kod dosyasında kesme noktalarını ayarlayın, hata ayıklayıcı başlatmak ve yerel bir SharePoint sitesi sayfasında herhangi bir ek yapılandırma adımı gerçekleştirmeden sınayın. Daha fazla bilgi için bkz: [oluşturma uygulama sayfaları SharePoint'in](../sharepoint/creating-application-pages-for-sharepoint.md).  
  
## <a name="create-site-pages-master-pages-and-page-layouts"></a>Site sayfaları, ana sayfalar ve sayfa düzenleri oluşturma
 SharePoint Designer kullanarak site sayfalar, ana sayfalar ve sayfa düzenleri oluşturabilirsiniz. Ardından, bu sayfaları Visual Studio'ya içeri aktarabilirsiniz. Visual Studio'da kullanılabilir kaynak denetimi özellikleri ve dağıtım yararlanmak isterseniz sayfalarınızı içeri aktarın. Daha fazla bilgi için bkz: [var olan bir SharePoint sitesinden öğeleri içeri aktarma](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
 Aldıktan sonra bu sayfaları değiştirmek zor olduğundan, bunları içeri aktarmadan önce bu sayfaları tasarlamanız gerekir.  
  
## <a name="create-cascading-style-sheets-ecmascript-and-themes"></a>Geçişli stil sayfaları, ECMAScript ve Temalar oluşturma
 Visual Studio şablonları için geliştirme geçişli stil sayfaları (CSS), ECMAScript (JavaScript, JScript) veya tema dosyaları SharePoint siteleri için sağlamaz. SharePoint SDK'ın yönelik Kılavuzlar kullanarak veya SharePoint Designer gibi araçları kullanarak, bu dosyaları oluşturabilirsiniz.  
  
 Bu dosyaları doğrudan çözümünüze ekleyebilir veya içeri aktarabilirsiniz. Her iki durumda da, eklediğiniz her bir öğe için uygun eşlenen klasörler oluşturmanız gerekir. Eşlenmiş bir klasör oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: eşlenmiş klasörler ekleyip](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
 Geçişli stil sayfaları oluşturma hakkında daha fazla bilgi için bkz: [geçişli stil sayfaları sınıfı kullanımı SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkID=182098). Bir SharePoint çözüm için JavaScript ve JScript dosyaları oluşturma hakkında daha fazla bilgi için bkz: [ayarı oluşturan bir temel ASPX sayfa ECMAScript için](http://go.microsoft.com/fwlink/?LinkID=182099). Temalar hakkında daha fazla bilgi için bkz: [yapı taşı: sayfaları ve kullanıcı arabirimi](http://go.microsoft.com/fwlink/?LinkID=182095).  
  
## <a name="related-topics"></a>İlgili konular
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)|Uygulama sayfaları eklemeyi açıklar: *.aspx* SharePoint ana sayfa ile birleştirilmiş içeriği.|  
|[Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md)|Bir SharePoint sitesinde çalıştırmak ASP.NET sayfalarının nasıl oluşturulacağını gösterir.|  
|[İzlenecek yol: SharePoint uygulama sayfası oluşturma](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)|Tasarımı ve hata ayıklama bir SharePoint sitesi için bir ASP.NET Web sayfası gösterilir.|  
  
