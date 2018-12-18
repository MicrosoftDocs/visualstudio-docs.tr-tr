---
title: ClickOnce ile COM bileşenleri dağıtma | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- registration-free COM deployment
- ClickOnce deployment, COM components
- COM components, deploying
- deploying applications [ClickOnce], COM components
- components, deploying
ms.assetid: 1a4c7f4c-7a41-45f2-9af4-8b1666469b89
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e81462b2ccb5d29a0090623d72cf78183abd6917
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348753"
---
# <a name="deploy-com-components-with-clickonce"></a>ClickOnce ile COM bileşenleri dağıtma
Eski COM bileşenlerinin dağıtımını, geleneksel olarak zor bir görev olmuştur. Bileşenleri, genel olarak kaydedilmesi gerekir ve bu nedenle çakışan uygulamalar arasında istenmeyen yan etkilere neden olabilir. Bileşenler bir uygulama için tamamen yalıtılmış veya yan yana uyumludur. çünkü bu durum genellikle .NET Framework uygulamalarında bir sorun değildir. Visual Studio yalıtılmış COM bileşenlerini Windows XP ya da daha yüksek işletim sistemi dağıtmanıza olanak tanır.  
  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .NET uygulamaları dağıtmak için kolay ve güvenli bir mekanizma sağlar. Ancak, uygulamalarınızı eski COM bileşenleri kullanıyorsanız, bunları dağıtmak için ek adımlar uygulamanız gerekir. Bu konuda, yalıtılmış COM bileşenlerini dağıtmak ve yerel bileşenlerin (örneğin, Visual Basic 6.0 veya Visual C++) başvuru açıklar.  
  
 Yalıtılmış COM bileşenleri dağıtma ile ilgili daha fazla bilgi için bkz: [ClickOnce ve Registration-Free COM ile uygulama dağıtımını basitleştirmeye](https://web.archive.org/web/20050326005413/msdn.microsoft.com/msdnmag/issues/05/04/RegFreeCOM/default.aspx).
  
## <a name="registration-free-com"></a>Kayıtsız COM  
 Kayıtsız COM dağıtımı ve yalıtılmış COM bileşenlerini etkinleştirme için yeni bir teknolojidir. Bileşenin tüm tür kitaplığı ve genellikle bir bildirim adlı bir XML dosyasına sistem kayıt defterine yüklenir kayıt bilgileri koyarak çalıştığı uygulama ile aynı klasörde depolanır.  
  
 Bir COM bileşeni yalıtma Geliştirici makinesinde kayıtlı olması gerekir, ancak son kullanıcının bilgisayarda kayıtlı olması gerekmez. Bir COM bileşeni yalıtmak için tüm yapmanız gereken ayarlamak, başvurusunun **yalıtılmış** özelliğini **True**. Varsayılan olarak, bu özellik kümesine **False**, kayıtlı bir COM başvurusu olarak değerlendirilmesi gerektiğini belirten. Bu özellik ise **True**, oluşturma zamanında bu bileşen için oluşturulacak bildirim neden olur. Yükleme sırasında uygulama klasörüne kopyalanacak karşılık gelen dosyalar neden olur.  
  
 Bildirim oluşturucu yalıtılmış bir COM başvurusu karşılaştığında, tüm numaralandırır `CoClass` girişleri bileşenin tür kitaplığındaki her girişin karşılık gelen kayıt verilerini ile eşleşen ve oluşturma bildirimi tüm COM tanımları tür kitaplığı dosyasının sınıfları.  
  
## <a name="deploy-registration-free-com-components-using-clickonce"></a>Kayıtsız COM bileşenlerini ClickOnce kullanarak dağıtma  
 [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dağıtım teknolojisidir yalıtılmış COM bileşenlerini dağıtmak için uygundur çünkü her ikisi de [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] ve kayıt gerektirmeyen COM gerekli bir bileşen dağıtılması için bir bildirim olması.  
  
 Genellikle, yazarı bileşenin bir bildirim sağlamanız gerekir. Aksi durumda, ancak Visual Studio otomatik olarak bir COM bileşeni için bir bildirim oluşturma yeteneğine sahiptir. Bildirim oluşturulması sırasında gerçekleştirilen [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlama işlemi; daha fazla bilgi için [ClickOnce uygulamalarını yayımlama](../deployment/publishing-clickonce-applications.md). Bu özellik, Visual Basic 6.0 gibi önceki geliştirme ortamlarında yazılan eski bileşenleri yararlanmanıza olanak tanır.  
  
 İki yolu vardır, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] COM bileşenlerini dağıtır:  
  
-   Önyükleyici, COM bileşenlerini dağıtmak için kullanın. Bu, desteklenen tüm platformlarda çalışır.  
  
-   Yerel bileşen yalıtım (diğer adıyla kayıt gerektirmeyen COM) dağıtımı kullanın. Ancak, bu yalnızca bir Windows XP veya üzeri işletim sistemi üzerinde çalışır.  
  
### <a name="example-of-isolating-and-deploying-a-simple-com-component"></a>Yalıtma ve basit bir COM bileşeni dağıtma örneği  
 Kayıtsız COM bileşeni dağıtımı göstermek için bu örnekte Visual Basic 6.0 kullanılarak oluşturulan bir yalıtılmış yerel COM bileşenine başvurduğunu Visual Basic'te Windows tabanlı bir uygulama oluşturma ve kullanarak [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Önce yerel bir COM bileşeni oluşturmanız gerekecektir:  
  
##### <a name="to-create-a-native-com-component"></a>Yerel bir COM bileşeni oluşturma  
  
1.  Visual Basic 6.0 kullanarak **dosya** menüsünde tıklatın **yeni**, ardından **proje**.  
  
2.  İçinde **yeni proje** iletişim kutusunda **Visual Basic** düğümünü seçip alt bir **ActiveX DLL** proje. İçinde **adı** kutusuna `VB6Hello`.  
  
    > [!NOTE]
    >  Kayıtsız COM yalnızca ActiveX DLL ve ActiveX denetimi projesi türleri desteklenir; ActiveX EXE ve ActiveX belgesi proje türleri desteklenmez.  
  
3.  İçinde **Çözüm Gezgini**, çift **Class1.vb** metin düzenleyiciyi açın.  
  
4.  Class1.vb içinde için üretilen koddan sonra aşağıdaki kodu ekleyin. `New` yöntemi:  
  
    ```vb  
    Public Sub SayHello()  
       MsgBox "Message from the VB6Hello COM component"  
    End Sub  
    ```  
  
5.  Bileşen oluşturun. Gelen **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
> [!NOTE]
>  Kayıtsız COM DLL'leri yalnızca destekler ve proje türleri COM denetler. Kayıtsız COM exe kullanamazsınız  
  
 Artık Windows tabanlı bir uygulama oluşturun ve COM bileşenine bir başvuru ekleyin.  
  
##### <a name="to-create-a-windows-based-application-using-a-com-component"></a>Bir COM bileşeni kullanarak Windows tabanlı bir uygulama oluşturmak için  
  
1. Visual Basic kullanarak **dosya** menüsünde tıklatın **yeni**, ardından **proje**.  
  
2. İçinde **yeni proje** iletişim kutusunda **Visual Basic** düğümünü seçip alt **Windows uygulama**. İçinde **adı** kutusuna `RegFreeComDemo`.  
  
3. İçinde **Çözüm Gezgini**, tıklayın **tüm dosyaları göster** proje başvurularını görüntülenecek düğmesi.  
  
4. Sağ **başvuruları** düğümünü seçip alt **Başvuru Ekle** bağlam menüsünden.  
  
5. İçinde **Başvuru Ekle** iletişim kutusu, tıklayın **Gözat** sekmesine VB6Hello.dll'e gidin ve ardından seçin.  
  
    A **VB6Hello** başvurusu, başvuruları listesinde belirir.  
  
6. İşaret **araç kutusu**seçin bir **düğmesi** denetlemek ve sürükleyin **Form1** formu.  
  
7. İçinde **özellikleri** penceresinde ayarlayın düğmenin **metin** özelliğini **Hello**.  
  
8. İşleyici kodu eklemek için Ekle düğmesine çift tıklayın ve işleyicisi aşağıdaki gibi görünür, böylece kod dosyasında, kodu ekleyin:  
  
   ```vb  
   Private Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim VbObj As New VB6Hello.Class1  
       VbObj.SayHello()  
   End Sub  
   ```  
  
9. Uygulamayı çalıştırın. Gelen **hata ayıklama** menüsünü tıklatın **hata ayıklamayı Başlat**.  
  
   Sonraki denetimi ayırmanız gerekir. Uygulamanızın kullandığı her bir COM bileşeni projenize bir COM başvurusu olarak temsil edilir. Bu başvurular altında görülebilir **başvuruları** düğümünde **Çözüm Gezgini** penceresi. (Ekleyebileceğiniz bildirimi başvuran ya da kullanarak doğrudan **Başvuru Ekle** komutunu **proje** menüsünden veya dolaylı olarak bir ActiveX denetimini formunuza sürükleyerek.)  
  
   Aşağıdaki adımlarda, COM bileşeni yalıtmak ve yalıtılmış denetimi içeren güncelleştirilmiş uygulamayı yayımlamak gösterilmektedir:  
  
##### <a name="to-isolate-a-com-component"></a>Bir COM bileşeni ayırmak için  
  
1. İçinde **Çözüm Gezgini**, **başvuruları** düğümünü **VB6Hello** başvuru.  
  
2. İçinde **özellikleri** penceresinde değiştirin **yalıtılmış** özelliğinden **False** için **True**.  
  
3. Gelen **derleme** menüsünde tıklatın **Çözümü Derle**.  
  
   Şimdi ne zaman uygulama beklendiği gibi çalıştığını F5 tuşuna basın, ancak artık Kayıtsız COM altında çalışıyor Bu, kanıtlamak için VB6Hello.dll bileşen kaydı RegFreeComDemo1.exe Visual Studio IDE dışında çalıştırmayı deneyin. Düğme tıklandığında bu süre hala çalışır. Uygulama bildirimi geçici olarak yeniden adlandırma, yeniden başarısız olur.  
  
> [!NOTE]
>  Geçici olarak kaydını silerek bir COM bileşeni olmaması benzetimini yapabilirsiniz. Bir komut istemi açın, yazarak sistem klasörünüze gidin `cd /d %windir%\system32`, ardından yazarak bileşeninin kaydı `regsvr32 /u VB6Hello.dll`. Yeniden yazarak kaydedebilirsiniz `regsvr32 VB6Hello.dll`.  
  
 Kullanarak uygulamayı yayımlamak için son adımdır [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]:  
  
##### <a name="to-publish-an-application-update-with-an-isolated-com-component"></a>Yalıtılmış bir COM bileşeni ile bir uygulama güncelleştirmesi yayımlamak için  
  
1. Gelen **derleme** menüsünde tıklatın **yayımlama RegFreeComDemo**.  
  
    Yayınla Sihirbazı görüntülenir.  
  
2. Yayımlama Sihirbazı'nda, burada erişebilir ve yayımlanan dosyaları incelemek yerel bilgisayarın diskte bir konum belirtin.  
  
3. Tıklayın **son** uygulamayı yayınlamak için.  
  
   Yayımlanan dosyaları incelemek, sysmon.ocx dosyasının dahil olduğunu fark edeceksiniz. Denetim, son kullanıcının makinede denetiminin farklı bir sürümü kullanılarak başka bir uygulama varsa, bu uygulamayla kesintiye neden olamaz, yani bu uygulama, tamamen yalıtılır.  
  
## <a name="reference-native-assemblies"></a>Yerel başvuru derlemeleri  
 Visual Studio yerel Visual Basic 6.0 veya C++ derlemelerin başvurularını destekler. Yerel başvurular böyle başvurular çağrılır. Olduğunu doğrulayarak, bir başvuru yerel olup olmadığını, **dosya türü** özelliği **yerel** veya **ActiveX**.  
  
 Yerel bir başvuru eklemek için **Başvuru Ekle** komutunu ve ardından bildirime göz atın. Bazı bileşenler bildirimi DLL içine yerleştirin. Bu durumda, yalnızca DLL seçebilirsiniz ve Visual Studio bileşeni gömülü bir bildirim içeren algılarsa yerel bir başvuru olarak ekleyecektir. Visual Studio, herhangi bir bağımlı dosyaları veya başvurulan bir bileşen olarak aynı klasörde olmaları durumunda bildiriminde listelenen derlemeleri de otomatik olarak dahil edilir.  
  
 COM denetimi yalıtım bildirimleri henüz COM bileşenlerini dağıtmak kolaylaştırır. Ancak, bir bileşen içeren bir bildirimi sağlanırsa, bildirim doğrudan başvurabilirsiniz. Aslında, her zaman mümkün olduğunda yerine bileşeninin yazarı tarafından sağlanan bildirimi kullanmalısınız **yalıtılmış** özelliği.  
  
## <a name="limitations-of-registration-free-com-component-deployment"></a>Kayıtsız COM bileşeni dağıtımı sınırlamaları  
 Kayıtsız COM dağıtımı geleneksel teknikler Temizle avantajları sunar. Ancak, bazı sınırlamalar ve ayrıca işaret edilmesi gereken uyarılar vardır. Yalnızca Windows XP veya üzeri sürümde çalışır durumda olduğunu büyük sınırlamasıdır. Kayıtsız COM uygulaması bileşenlerin çekirdek işletim sisteminde yüklü olan şekilde değişiklikler gereklidir. Ne yazık ki, alt düzey destek katmanı Kayıtsız COM için yok  
  
 Her bileşen Kayıtsız COM için uygun bir adaydır Aşağıdakilerden biri doğruysa, bir bileşenin bir uygun değil:  
  
- Bir işlem dışı sunucu bileşendir. EXE sunucuları desteklenmez; yalnızca dll desteklenir.  
  
- Bileşen, işletim sisteminin parçası olan veya XML, Internet Explorer veya Microsoft Data Access Components (MDAC) gibi bir sistem bileşeni. Yeniden dağıtım ilkesi bileşen yazarının izlemelidir; satıcınızla denetleyin.  
  
- Bileşen bir uygulama, Microsoft Office gibi bir parçasıdır. Örneğin, Microsoft Excel nesne modeline yalıtmak çalışmamalıdır. Bu Office bir parçasıdır ve yalnızca tam Office ürünü yüklü bir bilgisayarda kullanılabilir.  
  
- Bileşen bir eklenti veya bir ek bileşeni, örneğin bir Office Eklentisi veya bir Web tarayıcısında bir denetim olarak kullanılmak üzere tasarlanmıştır. Bu bileşenler, genellikle kayıt düzeni bildirim kapsamı dışında barındırma ortamı tarafından tanımlanan bir tür gerektirir.  
  
- Bileşen, system, örneğin, yazdırma biriktiricisi bir aygıt sürücüsü için fiziksel veya sanal bir cihaz yönetir.  
  
- Yeniden dağıtılabilir veri erişim bileşendir. Veri uygulamaları, genellikle ayrı veri çalıştırılmadan önce yüklenecek erişim yeniden dağıtılabilir gerektirir. Microsoft ADO veri denetimi, Microsoft OLE DB veya Microsoft Data Access Components (MDAC) gibi bileşenleri yalıtmak çalışmamalıdır. Uygulamanız MDAC veya SQL Server Express kullanıyorsa, bunun yerine, önkoşul olarak ayarlamalısınız; bkz: [nasıl yapılır: ClickOnce uygulamasıyla Önkoşulları Yükleme](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
  Bazı durumlarda, kayıt gerektirmeyen com için baştan tasarlama şansını Geliştirici bileşen için olası olabilir Bu mümkün değilse, yine de derleme ve bunlara bağımlı önyükleyici kullanarak standart kayıt düzeni ile uygulama yayımlama. Daha fazla bilgi için [önyükleyici paketleri oluşturma](../deployment/creating-bootstrapper-packages.md).  
  
  Bir COM bileşeni yalnızca uygulama başına bir kez yalıtılmış olabilir. Örneğin, iki farklı aynı COM bileşeni ayıramazsınız **sınıf kitaplığı** aynı uygulamanın parçası olan projeleri. Bunun yapılması, bir yapı uyarısına neden olur ve uygulama çalışma zamanında yüklenmesi başarısız olur. Bu sorundan kaçınmak için Microsoft, bir tek Sınıf Kitaplığı'nda COM bileşenlerini kapsülleyen önerir.  
  
  Uygulamanın dağıtım kayıt gerektirmez rağmen COM Geliştirici makinesinde, kayıt gereken birkaç senaryo mevcuttur. `Isolated` Özellik için otomatik olarak bildirim sırasında derleme oluşturmak için COM bileşeni Geliştirici makinesinde kayıtlı olması gerekir. Yapı sırasında kendi kendine kayıt çağıran hiçbir kayıt yakalama özellikleri vardır. Ayrıca, açıkça tür kitaplığında tanımlanan herhangi bir sınıf bildiriminde yansıtılmaz. Bir COM bileşeni ile yerel bir başvuru gibi önceden varolan bir bildirimi kullanırken Bileşen geliştirme zamanında kayıtlı olması gerekmeyebilir. Kayıt bir ActiveX denetimini bileşendir ve olmasını istiyorsanız ancak gereklidir **araç kutusu** ve Windows Forms Tasarımcısı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)