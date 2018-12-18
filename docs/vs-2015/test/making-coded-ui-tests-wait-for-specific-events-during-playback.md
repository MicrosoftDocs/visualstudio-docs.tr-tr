---
title: Kodlanmış UI yapma, kayıttan yürütme sırasında belirli olaylar için bekleme testleri | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 41981ad6-673e-492e-b739-9863b14157b1
caps.latest.revision: 26
ms.author: gewarren
manager: douge
ms.openlocfilehash: 0042be9e22b4143021b78cb96b6032144bd624f5
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941015"
---
# <a name="making-coded-ui-tests-wait-for-specific-events-during-playback"></a>Kayıttan Yürütme Sırasında Belirli Olaylar için Kodlanmış UI Testlerini Bekletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir kodlanmış UI Testi kayıttan yürütmesinde kaybolur ve benzeri için ilerleme çubuğunu oluşmasına görünmesi için bir pencere gibi belirli olaylar için beklenecek test bildirebilirsiniz. Bunu yapmak için aşağıdaki tabloda açıklandığı gibi uygun UITestControl.WaitForControlXXX() yöntemi kullanın. Bir denetimi kullanarak etkin olmasını bekler bir kodlanmış UI testine ilişkin bir örnek <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A> yöntemi bkz [izlenecek yol: oluşturma, düzenleme ve bir kodlanmış UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 **Gereksinimler**  
  
 Visual Studio Enterprise  
  
> [!TIP]
>  Kodlanmış UI Test düzenleyicisini kullanarak Eylemler önce gecikmelere de ekleyebilirsiniz. Daha fazla bilgi için [nasıl yapılır: bir gecikme önce bir UI eylemini kullanarak kodlanmış UI Test Düzenleyicisi Ekle](http://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0).  
  
 **UITestControl.WaitForControlXXX() yöntemleri**  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlReady%2A>  
  
 Denetim için fare ve klavye girdisi kabul etmeye hazır olmasını bekler. Altyapı denetimi, herhangi bir işlem yapmadan önce hazır olmasını beklemek için bu API tüm eylemler için örtük olarak çağırır. Ancak, bazı nadir bulunan bir senaryoda, açık bir çağrı yapmanız gerekebilir.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlEnabled%2A>  
  
 Denetimi Sihirbazı sunucuya çağrıları yaparak bazı zaman uyumsuz doğrulama giriş, etkin olmasını bekler. Beklenecek yöntemi gibi yapabilecekleriniz **sonraki** düğmesi etkin () olacak şekilde Sihirbazı. Bu yöntem bir örnek için bkz [izlenecek yol: oluşturma, düzenleme ve bir kodlanmış UI testi koruma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md).  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlExist%2A>  
  
 Kullanıcı Arabirimi üzerindeki görüntülenmesini denetim için bekler. Örneğin, uygulamanın doğrulama parametrelerinin tamamladıktan sonra bir hata iletişim kutusu bekliyorsunuz. Doğrulama için geçen süre değişkendir. Hata iletişim kutusunu beklemek için bu yöntemi kullanabilirsiniz.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlNotExist%2A>  
  
 Kullanıcı Arabiriminden kayboluyor denetimi için bekler. Örneğin, kaybolmuş ilerleme çubuğunun tamamlanmasını bekleyebilirsiniz.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyEqual%2A>  
  
 Verilen değer sağlamak için denetimi belirtilen özellik için bekler. Örneğin, durum metni değiştirmek beklemeniz **Bitti**.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlPropertyNotEqual%2A>  
  
 Belirtilen değere tam tersi için denetimin belirtilen özellik için bekler. Örneğin, salt okunur olmaması için düzenleme kutusuna diğer bir deyişle, bekleme düzenlenebilir.  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForControlCondition%2A>  
  
 Belirtilen önerme olmasını döndürür bekler `true`. Bu, karmaşık bekleme işlemi (veya koşulları gibi) belirli bir denetim için kullanılabilir. Örneğin, durum metni kadar bekleyebilirsiniz **başarılı** veya **başarısız** aşağıdaki kodda gösterildiği gibi:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDone(UITestControl control)   
{   
    WinText statusText = control as WinText;   
    return statusText.DisplayText == "Succeeded" || statusText.DisplayText == "Failed";   
}   
  
// In test method, wait till the method evaluates to true   
statusText.WaitForControlCondition(IsStatusDone);  
  
```  
  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.WaitForCondition%2A>  
  
 Önceki tüm yöntemler, UITestControl, örnek yöntemlerdir. Bu yöntem statik bir yöntemdir. Bu yöntem ayrıca belirtilen bir koşulu olmasını bekler `true` ancak birden çok denetimin (veya koşulları gibi) karmaşık bekleme işlemi için kullanılabilir. Örneğin, durum metni kadar bekleyebilirsiniz **başarılı** veya aşağıdaki kodda gösterildiği gibi bir hata iletisi görünene kadar:  
  
```csharp  
  
// Define the method to evaluate the condition   
private static bool IsStatusDoneOrError(UITestControl[] controls)   
{   
    WinText statusText = controls[0] as WinText;   
    WinWindow errorDialog = controls[1] as WinWindow;   
    return statusText.DisplayText == "Succeeded" || errorDialog.Exists;   
}   
  
// In test method, wait till the method evaluates to true   
UITestControl.WaitForCondition<UITestControl[]>(new UITestControl[] { statusText, errorDialog }, IsStatusDoneOrError);  
  
```  
  
 Bu yöntemlerin tümü, aşağıdaki davranışa sahiptir:  
  
 Yöntemler, bekleme başarısız olduysa bekleme başarılı false ise true döndürür.  
  
 Örtük zaman aşımı için bekleme işlemi tarafından belirtilen <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyTimeout%2A> özelliği. Bu özelliğin varsayılan değeri 60000 (bir dakika) milisaniyedir.  
  
 Açık zaman aşımı milisaniye içinde gerçekleştirilecek bir aşırı yükleme yöntemleri vardır. Ancak, bekleme işlemi örtülü bir arama denetimi için veya uygulama meşgul olduğunda sonuçları, gerçek bir bekleme süresi belirtilen zaman aşımı değeri fazla olabilir.  
  
 Önceki İşlevler, güçlü ve esnektir ve neredeyse tüm koşulları karşılaması gerekir. Ancak durumda bu yöntem, gereksinimlerinizi karşılamayan ve ya da kod gerekiyorsa bir <xref:Microsoft.VisualStudio.TestTools.UITesting.Playback.Wait%2A>, veya bir <xref:System.Threading.Thread.Sleep%2A> kodunuzda Playback.Wait() Thread.Sleep() API'si yerine kullanmanız önerilir. Bu nedenleri şunlardır:  
  
 Kullanabileceğiniz <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.ThinkTimeMultiplier%2A>uyku süresi değiştirmek için özellik. Varsayılan olarak, bu değişken 1'dir ancak artırıp kod karşısında bekleme süresini değiştirmek için azaltabilirsiniz. Örneğin, özellikle yavaş ağ veya diğer bir yavaş performans olay üzerinden test ediyorsanız, %1.5 50 ilave tüm konumlarda bekleyin eklemek için bu değişkeni, tek bir yerde (veya hatta yapılandırma dosyasında) değiştirebilirsiniz.  
  
 Playback.Wait() içten Thread.Sleep() çağırır (sonra hesaplama yukarıda) için-kullanıcı cancel\break işlemi için denetlenirken döngü içinde daha küçük öbekler halinde. Diğer bir deyişle, kayıttan yürütme ise bekleme bitiminden önce iptal Playback.Wait() uyku değil veya özel durum.  
  
> [!TIP]
>  Kodlanmış UI Test Düzenleyicisi'ni kullanarak kodlanmış UI testlerini kolayca değiştirmenize olanak tanır. Kodlanmış UI Test Düzenleyicisi'ni kullanarak bulun, görüntüleyin ve test yöntemlerinizi düzenleyin. UI eylemlerini ve bunların ilişkili denetimleri UI kontrol haritasında de düzenleyebilirsiniz. Daha fazla bilgi için [düzenleme kodlanmış UI Test düzenleyicisini kullanarak kodlanmış UI testleri](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md).  
  
 **Kılavuz**  
  
 Ek bilgi için bkz: [Testing for Continuous Delivery ile Visual Studio 2012 – Chapter 5: otomatikleşen sistem testleri](http://go.microsoft.com/fwlink/?LinkID=255196)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)   
 [Kodlanmış UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [İzlenecek yol: Oluşturma, düzenleme ve kodlanmış UI testi bakımını yapma](../test/walkthrough-creating-editing-and-maintaining-a-coded-ui-test.md)   
 [Kodlanmış UI testinin anatomisi](../test/anatomy-of-a-coded-ui-test.md)   
 [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)   
 [Nasıl yapılır: kodlanmış UI Test düzenleyicisini kullanarak bir UI eyleminden önce gecikme Ekle](http://msdn.microsoft.com/library/509f8ef7-e105-4049-b11b-d64549e055b0)



