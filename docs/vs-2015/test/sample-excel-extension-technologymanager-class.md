---
title: 'Örnek Excel uzantısı: TechnologyManager Sınıfı | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 11
ms.author: gewarren
manager: douge
ms.openlocfilehash: b23c3e735aba74d86b31afb4b83862d83bcd2bdb
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49190586"
---
# <a name="sample-excel-extension-technologymanager-class"></a>Örnek Excel Uzantısı: TechnologyManager Sınıfı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu sınıf genişletir <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager> sınıfı ve temel Hizmetleri için sağlamaktan sorumluysa [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] uzantısı. Temel sınıf birçok yöntem olsa da, bu örnekte yalnızca bir alt kümesini kullanılır.  
  
 Bazı yöntemler, yalnızca bir özellik değeri döndürür. Birçok yöntem, kodlanmış UI test motoruna algoritmaları yapı varsayılan geçersiz kılmak Geliştirici izin vermek için tasarlanmıştır. Bu yöntemler throw bir <xref:System.NotSupportedException> veya dönüş `null`, varsayılan algoritmasını kullanabilmesi için framework söyler.  
  
 Temel alınan teknoloji karmaşıklığına bağlı olarak, teknoloji Yöneticisi kodunuzu geliştirmek için birkaç ay birkaç hafta arasında bir seçim ele geçirebilir. Excel, potansiyel olarak çok geniş bir teknoloji Yöneticisi oluşturma fırsatı sağlar. Bu örnek, Excel çalışma sayfaları ve hücreler için kasıtlı olarak sınırlıdır ve sınırlı biçimlendirme kullanır.  
  
 Mümkün olduğunda, .NET uzaktan iletişim kanalı tarafından açıldı teknoloji Yöneticisi kodu kullanan `Communicator` bilgiler Excel işlemde çalışan içinde ayıklamak için sınıf.  
  
## <a name="com-visibility"></a>COM görünürlüğü  
 Bu sınıf ve her öğenin olduğuna dikkat edin genişletmek <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> tüm sınıf <xref:System.Runtime.InteropServices.ComVisibleAttribute> değeriyle `true` sınıfları için COM görünür olduğundan emin olmak için  
  
## <a name="technologyname-property"></a>TechnologyName özelliğini  
 Bu geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> özelliği, her bir bileşeni uzantısı için temel alınan teknoloji tanımlayan benzersiz ve anlamlı bir ad sağlamalısınız. Bu uzantı için "Excel" değeridir.  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel yöntemi  
 Bu geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> yöntemi teknoloji Yöneticisi sağlanan tanıtıcı tarafından temsil edilen denetim için sunduğu destek düzeyini gösteren bir sayı döndürür. Döndürülen değer, daha fazla teknoloji Yöneticisi denetimini destekler. Bu durumda, yöntem denetimi içeren bir pencere denetler ve Excel çalışma ise, yöntem en yüksek değeri döndürür; Aksi takdirde, hiçbir destek sağlandığını belirtir, sıfır döndürür.  
  
## <a name="methods-to-get-an-element"></a>Bir öğe almak için yöntemleri  
 Kodlanmış UI test çerçevesi tarafından bir tanıtıcı, bir ekran veya farklı bir teknoloji öğeden noktasında sağlayarak bir öğe teknolojiye özgü almak için kullanılan çeşitli önemli yöntemler vardır. Bu yöntemleri için kod değerleridir. Temel yöntemler aşağıdaki gibidir:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId yöntemi  
 Kodlanmış UI testi oluşturulduğunda kullanıcı testteki bazı veya tüm denetimler için özellik değerlerini belirtebilirsiniz. Bu özellik değerleri, test çerçevesi tarafından belirli kullanıcı Arabirimi denetimleri, test sırasında bulmak için kullanılan arama özellikleri olarak adlandırılan ad-değer çiftleri oluşturmak için kullanılır. Tüm arama özellikleri birlikte değerini temsil eden <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> teknolojisinde her denetimi içeren her bir öğenin özellik. Bir denetim, test sırasında birkaç kez bulunacak olabileceğinden, bu yöntem bir teknoloji Yöneticisi belirli bir denetim için arama özelliklerinin ayrıştırma iyileştirmeye yönelik bir yol sağlar. Bu yöntem ayrıca framework sonraki aramalar için bu denetim için kullanabileceğiniz bir tanımlama bilgisi döndürür. Bu yöntemi uygulaması kullanan <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> arama özellikleri ayrıştırmak için yöntemi.  
  
## <a name="matchelement-method"></a>MatchElement yöntemi  
 Bir teknoloji Yöneticisi tarafından denetim araması gerçekleştirmek için uygulayabileceğiniz <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> olası eşleşmeler bir dizi döndürür veya throw yöntemi <xref:System.NotSupportedException>, kendi arama algoritması kullanmak için framework söyler. Her iki durumda da, uygulamanız gereken <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A> yöntemi burada bu uygulamayı tekrar kullandığını <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> yöntemi.  
  
## <a name="navigation-methods"></a>Gezinti yöntemi  
 Bu yöntemler, üst, alt ve eşdüzey belirtilen öğe kullanıcı Arabirimi hiyerarşisinden alın. , Basit ve açıklamalı açıkça kodudur.  
  
## <a name="getexcelelement-internal-method"></a>GetExcelElement iç yöntemi  
 Bu iç yöntem bir pencere tutucu ve bir Excel öğe hakkında bilgi alır ve istenen Excel öğeyi döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Kodlanmış Kullanıcı Arabirimi Testlerini ve Eylem Kayıtlarını Microsoft Excel'i Desteklemek için Genişletme](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)



