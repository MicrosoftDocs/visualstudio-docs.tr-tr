---
title: ClickOnce uygulamalarını yerelleştirme | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a4234d8f6ee9fa946f2accfd50a587e6dbd8068
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822118"
---
# <a name="localize-clickonce-applications"></a>ClickOnce uygulamalarını yerelleştirme
Yerelleştirme, uygulamanızın belirli bir kültür için uygun hale getirme işlemidir. Bu işlem, kullanıcı arabirimi (UI) metni doğru tarih ve para birimi biçimlendirme, bir form üzerinde denetimleri boyutunu ayarlama kullanarak bir bölgeye özgü dile çevirme içerir ve gerekirse yansıtma denetimleri sağdan sola.  
  
 Bir veya daha fazla uydu derlemeleri oluşturma uygulama sonuçlarınızda yerelleştirme. Her derleme, kullanıcı Arabirimi dizeleri, resimler ve diğer kaynakları belirli bir kültüre özgü içerir. (Uygulamanızın ana yürütülebilir dosyanın uygulamanız için varsayılan kültürü dizeleri içerir.)  
  
 Bu konuda dağıtmak için üç yol açıklar bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] diğer kültürler için uygulama:  
  
-   Tek bir dağıtımda tüm uydu derlemelerini içerir.  
  
-   Her bulunan tek bir uydu derlemesi ile her bir kültür için bir dağıtım oluşturun.  
  
-   Uydu derlemelerini indirme.  
  
## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Tüm uydu derlemelerin bir dağıtımda  
 Yayımlama birden çok yerine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtımlarında, tek bir yayımlayabilirsiniz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] tüm uydu derlemelerini içeren dağıtım.  
  
 Varsayılan olarak bu yöntemdir [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. İçinde bu yöntemi kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ek bir iş yapmanız gerekmez.  
  
 Bu yöntemi kullanmak için *MageUI.exe*, uygulamanız için kültürü ayarlamanıza **nötr** içinde *MageUI.exe*. Ardından, el ile tüm uydu derlemeler, dağıtımınızdaki eklemeniz gerekir. İçinde *MageUI.exe*, uydu derlemelerini kullanarak ekleyebilirsiniz **Doldur** düğmesini **dosyaları** uygulama bildiriminizin sekmesi.  
  
 Bu yaklaşımın avantajı, tek bir dağıtımı oluşturur ve yerelleştirilmiş dağıtım sürecinizi basitleştirir içindir. Çalışma zamanında, uygun bir uydu derlemesini, kullanıcının Windows işletim sistemine bağlı olarak kullanılan varsayılan kültürü kullanılır. Bu yaklaşımın bir dezavantajı, uygulama yüklendiğinde veya güncelleştirildiğinde bir istemci bilgisayar üzerinde olduğunda, tüm uydu derlemeleri indirir ' dir. Uygulamanız çok sayıda dizeleri veya müşterilerinizin yavaş ağ bağlantınız varsa bu işlem sırasında uygulama güncelleştirmesi performansını etkileyebilir.  
  
> [!NOTE]
>  Bu yaklaşım, uygulamanızın yüksekliğini, genişliğini ve farklı kültürler farklı bir metin dizesi boyutlarının otomatik olarak uyum sağlayacak şekilde denetimleri konumunu ayarlar varsayar. Windows Forms denetimleri ve kolayca yerelleştirilebilir dahil olmak üzere bir form Tasarım olanak tanıyan teknolojileri çeşitli içeren <xref:System.Windows.Forms.FlowLayoutPanel> ve <xref:System.Windows.Forms.TableLayoutPanel> denetimlerin yanı sıra <xref:System.Windows.Forms.Control.AutoSize%2A> özelliği.  Ayrıca bkz: [nasıl yapılır: AutoSize ve TableLayoutPanel denetimini kullanarak Windows Forms'ta yerelleştirmeyi destekleme](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).  
  
## <a name="generate-one-deployment-for-each-culture"></a>Her bir kültür için bir dağıtım oluşturun  
 Bu dağıtım stratejisini içinde birden çok dağıtım oluşturun. Her dağıtımda, yalnızca belirli bir kültür için gereken uydu derleme içerir ve dağıtım kültüre özgü olarak işaretleyin.  
  
 İçinde bu yöntemi kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ayarlayın **Dili Yayımla** özelliği **Yayımla** istenen bölge için sekmesinde. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bölgeyi seçin ve diğer tüm uydu derlemelerin dağıtımdan hariç gerekli uydu derlemesini otomatik olarak içerir.  
  
 Kullanarak aynı şeyi gerçekleştirebilirsiniz *MageUI.exe* Microsoft aracında [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Kullanım **Doldur** düğmesini **dosyaları** uygulama bildiriminizi uygulama dizininden diğer tüm uydu derlemelerini hariç ve ardından ayarlamak için sekmesinde **kültür**alanına **adı** , dağıtım bildiriminde için sekmesinde *MageUI.exe*. Bu adımları yalnızca doğru uydu derlemesini içerir, ancak de ayarlar `language` özniteliği `assemblyIdentity` Dağıtım bildiriminizi kültüre karşılık gelen öğe.  
  
 Uygulamayı yayımladıktan sonra her ek kültür için bu adımı tekrarlamalısınız uygulamanızın desteklediği. Farklı bir Web sunucusu veya dosya paylaşımına her zaman her bir uygulama bildirimi farklı uydu derlemesi başvurur ve her dağıtım bildirimi içinfarklıbirdeğergerekirçünküyayımladığınızdaneminolmanızgerekir`language`özniteliği.  
  
## <a name="download-satellite-assemblies-on-demand"></a>Uydu derlemelerini indirme  
 Tüm uydu derlemeleri tek bir dağıtımda karar verirseniz, bu sayede derlemeleri isteğe bağlı olarak işaretlemek isteğe bağlı indirme, kullanarak performansı artırabilirsiniz. Uygulama yüklendiğinde veya işaretlenen derlemeler yüklenmeyecektir. Çağırarak gerektiğinde derlemeleri yükleyebilirsiniz <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> metodunda <xref:System.Deployment.Application.ApplicationDeployment> sınıfı.  
  
 Uydu derlemelerini indirme biraz isteğe bağlı derlemeleri diğer türleri farklıdır. Bu senaryoyu kullanarak etkinleştirme hakkında daha fazla bilgi ve kod örnekleri için [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] araçlarını [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], bakın [izlenecek yol: ClickOnce dağıtım API'si ile isteğe bağlı uydu derlemelerini indirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).  
  
 Bu senaryoda da etkinleştirebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Ayrıca bkz: [izlenecek yol: ClickOnce dağıtım API'sini kullanarak tasarımcı ile isteğe bağlı uydu derlemelerini indirme](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) veya [izlenecek yol: ClickOnce dağıtım API'si ile isteğe bağlı uydu derlemelerini indirme Tasarımcı kullanarak](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).  
  
## <a name="testing-localized-clickonce-applications-before-deployment"></a>Dağıtımdan önce yerelleştirilmiş ClickOnce uygulamalarını test etme  
 Bir Windows Forms uygulaması yalnızca şu durumlarda için bir uydu derlemesine kullanılacak <xref:System.Threading.Thread.CurrentUICulture%2A> özelliği uygulamanın ana iş parçacığı için uydu bütünleştirilmiş kodun kültüre ayarlayın. Yerel bir pazarda müşteri büyük olasılıkla zaten Windows yerelleştirilmiş bir sürümünü kültüre uygun varsayılan olarak ayarlanmış olan çalıştırırsınız.  
  
 Uygulamanızın müşteriler için kullanılabilir hale getirmeden önce yerelleştirilmiş dağıtımları test etmek için üç seçeneğiniz vardır:  
  
- Çalıştırabileceğiniz, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygun bir uygulama yerelleştirilmiş Windows sürümleri.  
  
- Ayarlayabileceğiniz <xref:System.Threading.Thread.CurrentUICulture%2A> program aracılığıyla uygulamanızdaki özelliği. (Bu özelliği çağırmadan önce ayarlanmalıdır <xref:System.Windows.Forms.Application.Run%2A> yöntemi.)  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [\<assemblyIdentity > öğesi](../deployment/assemblyidentity-element-clickonce-deployment.md)   
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)   
 [Windows forms globalize](/dotnet/framework/winforms/advanced/globalizing-windows-forms)