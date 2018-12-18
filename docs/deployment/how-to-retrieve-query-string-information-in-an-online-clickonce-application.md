---
title: 'Nasıl yapılır: bir çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, query strings
- query strings, retrieving information
ms.assetid: 48ce098a-a075-481b-a5f5-c8ba11f63120
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9e8ad899d7cf62b2d874d5dc4971c8e7ad7f950a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49829774"
---
# <a name="how-to-retrieve-query-string-information-in-an-online-clickonce-application"></a>Nasıl yapılır: çevrimiçi bir ClickOnce uygulamasında sorgu dize bilgilerini alma
*Sorgu dizesi* soru biçiminde rastgele bilgi içeren işareti (?) ile başlayan bir URL kısmıdır *ad = değer*. Sahip olduğunuz varsayalım bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] adlı uygulama `WindowsApp1` üzerinde barındıran `servername`, ve değişken için bir değer geçirmek istediğiniz `username` zaman uygulamasını başlatır. URL'niz aşağıdakine benzeyebilir:  
  
 `http://servername/WindowsApp1.application?username=joeuser`  
  
 Aşağıdaki iki yordamdan kullanmayı gösteren bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] sorgu dize bilgilerini almak için uygulama.  
  
> [!NOTE]
>  Bir dosya paylaşımına veya yerel dosya sistemi kullanmak yerine HTTP kullanarak, uygulamanız başlatıldığında, bir sorgu dizesinde yalnızca bilgi geçirebilirsiniz.  
  
 İlk yordam gösterir nasıl, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama, uygulama başlatıldığında bu değerleri okumak için küçük bir kod parçasını kullanabilirsiniz.  
  
 Sonraki yordam nasıl yapılandırılacağı gösterilmektedir, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama MageUI.exe kullanarak sorgu dizesi parametreleri kabul edebilir. Uygulamanızı yayımlayın olduğunda bunu gerekecektir.  
  
> [!NOTE]
>  Bu özelliği etkinleştirmek için bir karar almadan önce bu konunun ilerleyen bölümlerindeki "Güvenlik" bölümüne bakın.  
  
 Nasıl oluşturulacağı hakkında daha fazla bilgi için bir [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım kullanarak *Mage.exe* veya *MageUI.exe*, bkz: [izlenecek yol: bir ClickOnce uygulamasını el ile dağıtmak](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
> [!NOTE]
>  .NET Framework 3.5 SP1'de başlayarak, komut satırı bağımsız değişkenleri için çevrimdışı geçirilecek mümkündür [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulama. Uygulamaya bağımsız değişkenler sağlamak istiyorsanız, kısayolu ile parametrelere geçirebilirsiniz. MS APPREF uzantısı.  
  
### <a name="to-obtain-query-string-information-from-a-clickonce-application"></a>Bir ClickOnce uygulamasında sorgu dize bilgilerini almak için  
  
1.  Aşağıdaki kod, projenizde yerleştirin. Bu işlev kodu için sırada System.Web başvuru ve eklemek olacaktır `using` veya `Imports` System.Web, System.Collections.Specialized ve System.Deployment.Application deyimleri.  
  
     [!code-csharp[ClickOnceQueryString#1](../deployment/codesnippet/CSharp/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.cs)]
     [!code-vb[ClickOnceQueryString#1](../deployment/codesnippet/VisualBasic/how-to-retrieve-query-string-information-in-an-online-clickonce-application_1.vb)]  
  
2.  Almak için önceden tanımlanmış bir işlevi çağırmak bir <xref:System.Collections.DictionaryBase.Dictionary%2A> , ada göre sıralanan sorgu dizesi parametreleri.  
  
### <a name="to-enable-query-string-passing-in-a-clickonce-application-with-mageuiexe"></a>Sorgu dizesi MageUI.exe ile ClickOnce uygulamasında geçirmeyi etkinleştirmek için  
  
1. .NET komut istemi açıp şunu yazın:  
  
   ```cmd  
   MageUI  
   ```  
  
2. Gelen **dosya** menüsünde **açın**ve dağıtım bildirimini açmak, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dosyası olan uygulama sonu `.application` uzantısı.  
  
3. Seçin **dağıtım seçenekleri** paneli sol taraftaki gezinti penceresinde ve seçin **uygulamaya geçirilecek parametreler URL'ye izin ver** onay kutusu.  
  
4. Gelen **dosya** menüsünde **Kaydet**.  
  
> [!NOTE]
>  Alternatif olarak, sorgu dizesi içinde geçirmeyi etkinleştirebilirsiniz [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]. Seçin **uygulamaya geçirilecek parametreler URL'ye izin ver** açarak bulunabilir onay kutusunu **proje özellikleri**u seçerek **Yayımla** sekmesine tıklayarak **Seçenekleri** düğmesini seçip ardından **bildirimlerini**.  
  
## <a name="robust-programming"></a>Güçlü programlama  
 Sorgu dizesi parametrelerini kullanırken dikkat etmenizi uygulamanıza nasıl yüklü ve etkin. Uygulama, kullanıcının bilgisayarında Web'den veya bir ağ paylaşımından yüklemek için yapılandırılmışsa, kullanıcı uygulamayı yalnızca bir kez URL aracılığıyla etkinleştirecektir olasıdır. Bundan sonra kullanıcı kısayolunu kullanarak uygulamanızı genellikle etkinleştirecektir **Başlat** menüsü. Sonuç olarak, uygulamanızın yaşam süresi boyunca sorgu dizesi bağımsız değişkenleri yalnızca bir kez alması sağlanır. Gelecekte kullanım için kullanıcının makinede bu bağımsız değişkenler depolamayı seçerseniz, güvenli bir şekilde depolamak için sorumlu olursunuz.  
  
 Uygulamanız yalnızca çevrimiçi ise, her zaman bir URL aracılığıyla etkinleştirilir. Bu durumda bile, ancak uygulamanızı sorgu dizesi parametresi eksik veya bozuk olması durumunda düzgün şekilde çalışabilmesi için yazılmış olmalıdır.  
  
## <a name="net-framework-security"></a>.NET Framework güvenliği  
 URL parametreleri izin, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] kullanmadan önce giriş kötü amaçlı karakter temizlemeyi düşünüyorsanız uygulama. Bir dize teklifleri, eğik çizgi veya noktalı virgül, örneğin katıştırılmış, rastgele veri işlemleri kullandıysanız bir veritabanında bir SQL sorgusunda filtrelenmemiş gerçekleştirebilir. Sorgu dizesi güvenliği hakkında daha fazla bilgi için bkz. [betik yararlanan genel bakış](https://msdn.microsoft.com/Library/772c7312-211a-4eb3-8d6e-eec0aa1dcc07).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce uygulamalarının güvenliğini sağlama](../deployment/securing-clickonce-applications.md)