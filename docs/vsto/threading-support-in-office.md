---
title: Office'te iş parçacığı desteği
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- multiple threads [Office development in Visual Studio]
- threading [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], threading support
- object models [Office development in Visual Studio], threading support
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 5aafdad425d611d7d57c2ae8e53e505d3522ba38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49871116"
---
# <a name="threading-support-in-office"></a>Office'te iş parçacığı desteği
  Bu makalede, iş parçacığı Microsoft Office nesne modeli içinde nasıl desteklendiği hakkında bilgi sağlar. Office nesne modeli iş parçacığı güvenli değildir, ancak Office bir çözümde birden çok iş parçacığı ile çalışmaya mümkündür. Office uygulamaları, Bileşen Nesne Modeli (COM) sunucularıdır. COM istemcilerinin COM sunucuları rastgele iş parçacıklarında arama olanak tanır. İş parçacığı güvenli olmayan COM sunucuları için COM yalnızca tek bir mantıksal iş parçacığı herhangi bir zamanda sunucuda yürütür, böylece eş zamanlı çağrılar serileştirmek için bir mekanizma sağlar. Bu mekanizma tek iş parçacıklı grup (STA) model olarak bilinir. Çağrıları seri hale getirilmiş olduğundan sunucu meşgul veya diğer çağrılar arka plan iş parçacığında işleme sırasında çağıranlar süre engellenebilir.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="knowledge-required-when-using-multiple-threads"></a>Bilgi Bankası birden çok iş parçacığı kullanırken gereklidir  
 Birden çok iş parçacığı ile çalışmak için şu yönlerini en az temel bilgiye sahip çoklu iş parçacığı kullanımı:  
  
- Windows API'leri  
  
- COM birden çok iş parçacıklı kavramları  
  
- Eşzamanlılık  
  
- Eşitleme  
  
- Hazırlama  
  
  Genel bilgiler hakkında çoklu iş parçacığı bakın [yönetilen iş parçacığı](/dotnet/standard/threading/).  
  
  Office ana STA içinde çalışır. Etkilerini anlama, birden çok iş parçacığı Office ile kullandığı anlamak mümkün kılar.  
  
## <a name="basic-multithreading-scenario"></a>Çoklu iş parçacığı kullanımı temel senaryo  
 Office çözümlerinde kod her zaman ana kullanıcı Arabirimi iş parçacığında çalışır. Uygulama performansını ayrı bir görev bir arka plan iş parçacığında çalıştırarak kesintisiz isteyebilirsiniz. İki görevi görünüşte tek seferde yerine daha yumuşak yürütme (birden çok iş parçacığı kullanmak için ana neden) sonuçlanmalıdır diğer tarafından izlenen bir görevi tamamlamak için hedeftir. Örneğin, olay kodunuz ana Excel kullanıcı Arabirimi iş parçacığında olabilir ve arka plan iş parçacığında bir sunucudan verileri toplar ve sunucu verilerle Excel kullanıcı arabirimini hücrelerde güncelleştiren bir görev çalışabilir.  
  
## <a name="background-threads-that-call-into-the-office-object-model"></a>Office nesne modeline çağrı arka plan iş parçacıkları  
 Arka plan iş parçacığı Office uygulaması için bir çağrı yaptığında, çağrı otomatik olarak STA sınırı ötesinde sıralanır. Ancak, Office uygulamasını kolaylaştırır arka plan iş parçacığı çağrı zaman işleyebileceğini garantisi yoktur. Birkaç olasılık vardır:  
  
1. Office uygulamasını fırsatınız girmek için çağrıyı iletileri göndermelidir. Yapıyorsa, bu ağır işlemeler zaman alabilir.  
  
2. Başka bir mantıksal iş parçacığı grubu ise, yeni iş parçacığı giremezsiniz. Bu durum, genellikle mantıksal iş parçacığı Office uygulamasına girdiğinde ve ardından bir desteklemeyeceğini geri arayanın apartman çağrıda oluşur. Uygulamayı döndürmek bu çağrı için bekleyen engellenir.  
  
3. Gelen bir çağrıyı hemen veremeyecek Excel bir durumda olabilir. Örneğin, Office uygulamasına kalıcı bir iletişim kutusu görüntüleniyor.  
  
   2. ve 3 olasılıkları için COM sağlar [ı](/windows/desktop/api/objidl/nn-objidl-imessagefilter) arabirimi. Sunucu uygularsa, tüm çağrılar aracılığıyla girer [HandleIncomingCall](/windows/desktop/api/objidl/nf-objidl-imessagefilter-handleincomingcall) yöntemi. 2 olasılığı için çağrıları otomatik olarak reddedilir. 3 olasılığı için sunucu koşullara bağlı olarak çağrı reddedebilirsiniz. Çağrı reddedilirse, çağırana ne yapılacağını karar vermeniz gerekir. Normalde, arayanın uygular [ı](/windows/desktop/api/objidl/nn-objidl-imessagefilter), bu durumda, reddetme tarafından size bildirilecektir [IMessageFilter](/windows/desktop/api/objidl/nf-objidl-imessagefilter-retryrejectedcall) yöntemi.  
  
   Ancak, Visual Studio'da Office geliştirme araçlarını kullanarak oluşturulan çözümleri söz konusu olduğunda, tüm reddedilen çağrılar COM birlikte çalışma dönüştürür bir <xref:System.Runtime.InteropServices.COMException> ("İleti Filtresi uygulama meşgul olduğunu gösterilen"). Nesne modeli çağrısı yaptığınızda bir arka plan iş parçacığı üzerinde bu özel durumu işlemek hazırlıklı olmanız gerekir. Genellikle, belirli bir miktar yeniden denemeyi ve ardından bir iletişim kutusu görüntülenirken içerir. Ancak, arka plan iş parçacığı STA olarak oluşturabilir ve ardından bu iş parçacığının bu durumu işlemek için ileti filtresini kaydetme.  
  
## <a name="start-the-thread-correctly"></a>İş parçacığının doğru Başlat  
 Yeni bir STA iş parçacığı oluşturduğunuzda, iş parçacığı başlamadan önce Grup durumu için STA ayarlayın. Aşağıdaki kod örneği, bunun nasıl yapılacağı gösterilmektedir.  
  
 [!code-csharp[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreCreatingExcelCS/ThisWorkbook.cs#5)]
 [!code-vb[Trin_VstcoreCreatingExcel#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreCreatingExcelVB/ThisWorkbook.vb#5)]  
  
 Daha fazla bilgi için [yönetilen iş parçacığı oluşturma en iyi yöntemleri](/dotnet/standard/threading/managed-threading-best-practices).  
  
## <a name="modeless-forms"></a>Kalıcı olmayan formlar  
 Form görüntülendiğinde geçici bir form herhangi bir türde uygulama ile etkileşim sağlar. Kullanıcı formla etkileşim ve formu kapatmadan uygulama etkileşime geçer. Yönetilen kalıcı olmayan formlar Office nesne modeli destekler. Ancak, bunlar bir arka plan iş parçacığı üzerinde kullanılmamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Yönetilen iş parçacığı oluşturma](/dotnet/standard/threading/)  
 [İş parçacığı oluşturma (C#)](/dotnet/csharp/programming-guide/concepts/threading/index) [(Visual Basic) iş parçacığı oluşturma](/dotnet/visual-basic/programming-guide/concepts/threading/index)   
 [Kullanım iş parçacıkları ve iş parçacığı oluşturma](/dotnet/standard/threading/using-threads-and-threading)   
 [Office çözümleri oluşturma ve tasarlama](../vsto/designing-and-creating-office-solutions.md)  
  
  