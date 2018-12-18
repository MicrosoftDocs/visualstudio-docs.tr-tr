---
title: VS 2017'de hata ayıklama kullanmaya başlayın
description: Visual Studio hata ayıklayıcısını kullanarak uygulamalarda hata ayıklamaya başlama
ms.custom: mvc
ms.date: 06/15/2018
ms.technology: vs-ide-debug
ms.topic: quickstart
helpviewer_keywords:
- debugger
ms.assetid: c763d706-3213-494f-b4d2-990b6e1ec456
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d5c479251b7002e506f1dff5e64a028875aa8f80
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49882672"
---
# <a name="first-look-at-the-visual-studio-debugger"></a>Visual Studio hata ayıklayıcı ilk bakış

Bu konu Visual Studio tarafından sağlanan hata ayıklayıcı araçları sunar. Visual Studio bağlamda olduğunda, *uygulamanızda hata ayıklama*, hata ayıklayıcısı ekli uygulamanın çalıştığını genellikle anlamına gelir (diğer bir deyişle, hata ayıklayıcı modunda). Bunu yaptığınızda, hata ayıklayıcı, kodunuzun ne yaptığını görmek için birçok yol sağlar. çalışırken. Kodunuzda adım adım ve değişkenlerinde depolanan değerleri bakmak, gözcüler değerler değiştiğinde görmek için değişkenleri ayarlayabilirsiniz, kodunuzun yürütme yolunu inceleyebilirsiniz tarayıcılarınızda. Bu, kodda hata ayıklamak için girişimde ilk kez ise, okumak isteyebilirsiniz [yeni başlayanlar için hata ayıklama](../debugger/debugging-absolute-beginners.md) Bu konu üzerinden geçmeden önce.

Burada açıklanan özellikler, C#, C++, Visual Basic, JavaScript ve (belirtilenler dışında) Visual Studio tarafından desteklenen diğer diller için geçerlidir.

## <a name="set-a-breakpoint-and-start-the-debugger"></a>Bir kesme noktası ayarlayın ve hata ayıklayıcıyı başlatın

Hata ayıklamak için uygulamanızı app eklemede hata ayıklayıcısı ile başlatmanız gerekir. **F5** (**hata ayıklama > hata ayıklamayı Başlat**) Bunun en yaygın yoludur. Ancak, uygulamanız incelemek için herhangi bir kesme noktası ayarlamış olabileceğiniz değil artık doğrudan kodlayın, biz bunu ilk olarak yapın ve ardından hata ayıklamayı başlatmak için. Kesme noktaları güvenilir hata ayıklama en temel hem de temel özelliğidir. Bir kesme noktası değişkenlerin değerleri veya bellek davranışını göz olabilmesi için Visual Studio çalışan kodunuzu nereye askıya almanız ya da bir dal kod getting run olup olmadığını gösterir. 

Kod Düzenleyicisi'nde bir dosya varsa, kod satırının sol kenar boşluğunu tıklayarak kesme noktası ayarlayabilirsiniz.

![Bir kesme noktası ayarlamak](../debugger/media/dbg-tour-set-a-breakpoint.gif "bir kesme noktası ayarlayın")

Tuşuna **F5** (**hata ayıklama > hata ayıklamayı Başlat**) veya **hata ayıklamayı Başlat** düğmesi ![hata ayıklamayı Başlat](../debugger/media/dbg-tour-start-debugging.png "hata ayıklamayı Başlat ") hata ayıklama araç çubuğu ve bulduğu ilk kesme noktasına hata ayıklayıcı çalışır. Uygulama henüz çalışmıyorsa, F5 hata ayıklayıcıyı başlatır ve ilk kesme noktasında durur.

Kod satırının veya ayrıntılı olarak incelemek istediğiniz kod bölümünün bildiğiniz durumlarda kesme noktaları yararlı bir özelliktir.

## <a name="navigate"></a> Kod adım komutları kullanarak hata ayıklayıcısında gidin

Gezinti uygulama kodunuzun daha hızlı hale getirdiklerinden ait çoğu komut klavye kısayollarını sunuyoruz. (Menü komutları parantez içinde gösterilen gibi eşdeğer komutlar.)

Hata ayıklayıcısı ekli uygulamanızı başlatmak için basın **F11** (**hata ayıklama > içine adımla**). F11 olan **içine adımla** komut ve aynı anda uygulama yürütme bir deyim ilerler. F11 ile uygulamayı başlattığınızda, hata ayıklayıcı üzerinde yürütülen ilk deyim keser.

![F11 Adımla](../debugger/media/dbg-tour-f11.png "F11 adım içine")

Sarı ok, aynı zamanda aynı noktayı (Bu bildirimi henüz çalıştırılmadı) uygulama yürütmeyi askıya alır, hata ayıklayıcı durduruldu, deyimi temsil eder.

F11 çoğu ayrıntılı yürütme akışı incelemek için iyi bir yoludur. (Daha hızlı kod boyunca taşımak için bazı diğer seçenekleri de gösteriyoruz.) Varsayılan olarak, kullanıcı dışı kod üzerinde hata ayıklayıcı atlar (daha ayrıntılı bilgi isterseniz bkz [yalnızca kendi kodum](../debugger/just-my-code.md)).

>[!NOTE]
> Yönetilen kodda özellikler ve işleçler (varsayılan davranış) otomatik olarak adımladığınızda bildirim almak isteyip istemediğinizi soran bir iletişim kutusu görürsünüz. Ayarı değiştirmek isterseniz daha sonra devre dışı **özellikleri ve işleçleri üzerinden adımla** ayarı **Araçlar > Seçenekler** menüsünün altında **hata ayıklama**.

## <a name="step-over-code-to-skip-functions"></a>İşlevleri atlamak için bir kod üzerinde Adım

Bir işlev veya metot çağırma kod satırında işiniz basabilirsiniz **F10** (**hata ayıklama > Step Over**) F11 yerine.

F10 işlevleri veya yöntemleri (kod hala çalışır), uygulama kodunuzda içine Adımlama olmadan, hata ayıklayıcı ilerler. F10 tuşlarına basarak, ilginizi olmadığınız bir kod üzerinde atlayabilirsiniz. Bu şekilde, hızlı bir şekilde daha ilgilendiğiniz kodu alabilirsiniz.

## <a name="step-into-a-property"></a>Bir özellikte adım

Hata ayıklayıcı, yönetilen özellikleri ve alanları üzerinden atlar varsayılan olarak daha önce belirtildiği gibi ancak **özel içine adımla** komutu bu davranışı geçersiz kılmanıza da olanak verir.

Bir özellik veya alan sağ tıklatın ve seçin **özel içine adımla**, sonra kullanılabilir seçeneklerden birini seçin.

![Belirli adım](../debugger/media/dbg-tour-step-into-specific.png "özel içine adımla")

Bu örnekte, **özel içine adımla** bize kodunu alır `Path.set`.

![Belirli adım](../debugger/media/dbg-tour-step-into-specific-2.png "özel içine adımla")

## <a name="run-to-a-point-in-your-code-quickly-using-the-mouse"></a>Fareyi kullanarak hızlı bir şekilde kodunuzda bir noktasına çalıştırın

Tarihine kadar kod satırının üzerine hata ayıklayıcısı olsa, **tıklanan satıra kadar Çalıştır** (yürütmeyi buraya Çalıştır) düğmesini ![tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click.png "RunToClick") soldaki bölmede görünür.

![Tıklanan satıra kadar Çalıştır](../debugger/media/dbg-tour-run-to-click-2.png "tıklanan satıra kadar Çalıştır")

> [!NOTE]
> **Tıklanan satıra kadar Çalıştır** (yürütmeyi buraya Çalıştır) düğmesidir yeni [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Tıklayın **tıklanan satıra kadar Çalıştır** (yürütmeyi buraya Çalıştır) düğmesi. Hata ayıklayıcı kod satırına tıklattığınız ilerler.

Bu düğmeyi kullanarak geçici bir kesme noktası ayarlayarak benzer. Bu komut ayrıca hızlı uygulama kodu görünür bir bölge içinde dolaşma için kullanışlıdır. Kullanabileceğiniz **tıklanan satıra kadar Çalıştır** herhangi bir açık dosya.

## <a name="advance-the-debugger-out-of-the-current-function"></a>Hata ayıklayıcı dışında geçerli işlevi ilerlemek

Bazen, hata ayıklama oturumunuzu devam eder ancak hata ayıklayıcı tüm yolculuk geçerli işlevi ilerlemek isteyebilirsiniz.

Tuşuna **Shift + F11** (veya **hata ayıklama > dışarı adımla**).

Bu komut, uygulama yürütmeyi devam ettirir (ve hata ayıklayıcı ilerler) geçerli işlev dönene kadar.

## <a name="run-to-cursor"></a>İmlece kadar Çalıştır

Tuşuna basarak hata ayıklayıcıyı **hata ayıklamayı Durdur** kırmızı düğme ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "hata ayıklamayı Durdur") veya **Shift**  +  **F5**.

Uygulamanıza kod satırının sağ tıklatın ve seçin **imlece kadar Çalıştır**. Bu komut, hata ayıklamasını başlatır ve geçerli kod satırında geçici bir kesme noktası ayarlar.

![İmlece kadar Çalıştır](../debugger/media/dbg-tour-run-to-cursor.png "imlece kadar Çalıştır")

Kesme noktası ayarlarsanız, hata ayıklayıcı, İsabetleri ilk kesme noktasına duraklatır.

Tuşuna **F5** seçtiğiniz kod satırının ulaşana kadar **imlece kadar Çalıştır**.

Bu komut, kod düzenleme ve hızlı bir geçici kesme noktası ayarlayın ve aynı anda hata ayıklayıcıyı başlatmak istediğinizde yararlıdır.

> [!NOTE]
> Kullanabileceğiniz **imlece kadar Çalıştır** içinde **çağrı yığını** ayıklarken penceresi.

## <a name="restart-your-app-quickly"></a>Uygulamanızı hızlı bir şekilde yeniden başlatın

Tıklayın **yeniden** ![yeniden uygulama](../debugger/media/dbg-tour-restart.png "yeniden uygulama") hata ayıklama araç çubuğu düğmesini (**Ctrl + Shift + F5**).

Bastığınızda **yeniden**, uygulama durdurup hata ayıklayıcı yerine zaman kaydeder. İlk kesme noktasına isabet kodu yürüterek, hata ayıklayıcı duraklatır.

Hata ayıklayıcıyı durdurun ve kod düzenleyicisine dönmek istiyorsanız, kırmızı Durdur basabilirsiniz ![hata ayıklamayı Durdur](../debugger/media/dbg-tour-stop-debugging.png "hata ayıklamayı Durdur") yerine düğme **yeniden**.

## <a name="inspect-variables-with-data-tips"></a>Veri ipuçları değişkenlerle inceleyin

Biraz kullanacağınızı biliyorsanız, Başlat (değişken) hata ayıklayıcı ile uygulama durumunu incelemek için iyi bir fırsat sahip. Değişkenleri incelemek özellik hata ayıklayıcının en kullanışlı özellikler bazıları ve bunu yapmanın farklı yolu vardır. Genellikle, hata ayıklama bir sorun açmayı denediğinde, değişkenleri belirli uygulama durumda sahip olmalarını beklediğiniz değer olup olmadığını depoladığını kullanıma bulmak çalışıyorsunuz.

Hata ayıklayıcısında duraklatıldıktan karşın, bir nesne fare ile üzerine gelin ve varsayılan özellik değerine bakın (Bu örnekte, dosya adı `market 031.jpg` varsayılan özellik değeri).

![Bir veri ipucunda görüntülemek](../debugger/media/dbg-tour-data-tips.gif "bir veri ipucunda görüntüleyin")

Tüm özelliklerini görmek için nesnesini genişletin (gibi `FullPath` özelliği bu örnekte).

Genellikle, hata ayıklama sırasında istediğiniz nesnelerin özellik değerlerini denetlemek için hızlı bir yol ve veri ipuçları yapmak için iyi bir yoludur.

> [!TIP]
> En desteklenen dillerde hata ayıklama oturumu ortasında kod düzenleyebilirsiniz. Daha fazla bilgi için bkz. [Düzenle ve devam et](../debugger/edit-and-continue.md).

## <a name="inspect-variables-with-the-autos-and-locals-windows"></a>Otolar ve yerel öğeler pencerelerinde değişkenlerle inceleyin

Hata ayıklama sırasında bakmak **Otolar** altındaki kod düzenleyicisi penceresi.

![Otolar penceresinde](../debugger/media/dbg-tour-autos-window.png "otomatik değişkenler penceresi")

İçinde **Otolar** penceresinde ile bunların geçerli değerini ve türlerinin değişkenleri boyunca görürsünüz. **Otolar** penceresi gösterir geçerli satırı veya önceki satır kullanılan tüm değişkenleri (C++'daki, pencere gösterir değişkenleri kod önceki üç satır. Dile özgü davranışı için belgeleri denetleyin).

> [!NOTE]
> JavaScript'te **Yereller** penceresi ancak desteklenen **Otolar** penceresi.

Ardından, bakmak **Yereller** penceresi. **Yereller** penceresi şu anda kapsamındaki değişkenleri gösterir.

![Yerel öğeler penceresinde](../debugger/media/dbg-tour-locals-window.png "yerel öğeler penceresi")

Bu örnekte, `this` nesneyi ve nesnenin `f` kapsam içindedir. Daha fazla bilgi için bkz. [Otolar ve yerel öğeler Windows İnceleme değişkenler](../debugger/autos-and-locals-windows.md).

## <a name="set-a-watch"></a>Bir izleme ayarlayın

Kullanabileceğiniz bir **Watch** penceresinin bir değişken (veya bir ifade) takip etmek istediğinizi belirtin.

Hata ayıklarken, bir nesneye sağ tıklayın ve seçin **Gözcü Ekle**.

![Gözcü penceresi](../debugger/media/dbg-tour-watch-window.png "İzleme penceresi")

Bu örnekte, ayarlanan bir izleme sahip `f` nesne ve hata ayıklayıcı geçerken değiştirme değeri görebilirsiniz. Diğer değişken pencerelerini aksine **Watch** windows her zaman, izlerken değişkenleri Göster (bunlar zaman kapsam dışına renkte).

Daha fazla bilgi için bkz. [izleme ve QuickWatch Windows kullanarak bir izleme ayarlayın](../debugger/watch-and-quickwatch-windows.md)

## <a name="examine-the-call-stack"></a>Çağrı yığınını inceleyin

Tıklayın **çağrı yığını** alt sağ bölmede açık varsayılan olarak, hata ayıklama sırasında penceresi.

![Çağrı yığını inceleyin](../debugger/media/dbg-tour-call-stack.png "çağrı yığınını inceleyin")

**Çağrı yığını** penceresi, yöntemleri ve işlevleri çağrılır sırasını gösterir. Geçerli işlev en üst satırına gösterir ( `Update` Bu örnekte yöntemi). İkinci satır gösteren `Update` çağırıldığı `Path.set` özelliği ve benzeri. Çağrı yığınını inceleyebilir ve bir uygulamanın yürütme akışını anlamanıza için iyi bir yoludur.

> [!NOTE]
> **Çağrı yığını** penceresi benzer hata ayıklama perspektifi için Eclipse gibi bazı IDE içinde.

Bir satır kod, kaynak koda bakmaktır gitmek için çift tıklayın ve hata ayıklayıcı tarafından denetlenmekte olan geçerli kapsamını da değişiklikler. Bu hata ayıklayıcı ilerleyin değil.

Sağ tıklama menülerden kullanabilirsiniz **çağrı yığını** başka şeyler için pencere. Örneğin, belirli işlevlere kesme noktaları ekleme, yeniden kullanıp uygulamanızın **imlece kadar Çalıştır**ve kaynak kodunu inceleyin gidin. Bkz: [nasıl yapılır: çağrı yığınını incelemek](../debugger/how-to-use-the-call-stack-window.md).

## <a name="exception"></a> Bir özel durum inceleyin

Uygulamanızı bir özel durum oluşturduğunda, hata ayıklayıcı özel durum oluşturan kod satırına alır.

![Özel durum Yardımcısı](../debugger/media/dbg-tour-exception-helper.png "özel durum Yardımcısı")

Bu örnekte, **özel durum Yardımcısı** size gösterir bir `System.Argument` özel durum ve yol geçerli bir biçimde değil bildiren bir hata iletisi. Bu nedenle, bir yöntem veya işlev bağımsız değişken üzerinde hata bildirin.

Bu örnekte, `DirectoryInfo` çağrı üzerinde depolanan boş bir dize hata verdi `value` değişkeni.

Özel durum Yardımcısı hatalarını ayıklamanıza yardımcı olacak harika bir özelliğidir. Hata ayrıntılarını görüntüleme gibi şeyler ve özel durum Yardımcısı ' bir izleme ekleyin. Veya, gerekirse, belirli özel durum koşullarını değiştirebilirsiniz.

> [!NOTE]
> Özel durum Yardımcısı özel durum Yardımcısı'nda yerini [!include[vs_dev15](../misc/includes/vs_dev15_md.md)].

Genişletin **özel durum ayarları** tur için herhangi bir ayarı değiştirmek bu özel durum türü, ancak işlemek nasıl daha fazla seçenek görmek için düğümü gerekmez!

## <a name="debug-live-aspnet-apps-in-azure-app-service"></a>Azure App Service'te Canlı ASP.NET uygulamalarının hatalarını ayıklama

**Snapshot Debugger** ilgilendiğiniz kod yürütüldüğünde, üretim uygulamalarınızı anlık görüntüsünü alır. Bir anlık görüntüsünü almak için hata ayıklayıcı açmasını sağlamak için anlık görüntü noktaları ve günlüğe kaydetme noktaları kodunuzda ayarlayın. Hata ayıklayıcı, tam olarak üretim uygulamanızın trafiğini etkilemeden, çıktığına görmenizi sağlar. Snapshot Debugger, üretim ortamlarında ortaya çıkan sorunları çözmek için gereken süreyi ciddi ölçüde azaltmaya yardımcı olabilir.

![Snapshot debugger'ı başlatma](../debugger/media/snapshot-launch.png "snapshot debugger'ı Başlat")

Anlık görüntü koleksiyonunu, Azure App Service'te çalışan ASP.NET uygulamaları için kullanılabilir. ASP.NET uygulamaları, .NET Framework 4.6.1 çalıştırıyor olması gerekir veya sonraki bir sürümü ve ASP.NET Core uygulamaları, .NET Core 2.0 veya daha sonra Windows üzerinde çalışmalıdır.

Daha fazla bilgi için [Snapshot Debugger'ı kullanarak canlı ASP.NET uygulamaları için hata ayıklama](../debugger/debug-live-azure-applications.md).

## <a name="view-snapshots-with-intellitrace-step-back-visual-studio-enterprise"></a>IntelliTrace geri adım atma (Visual Studio Enterprise) ile anlık görüntüleri Göster

**IntelliTrace geri adım** otomatik olarak adım olay her bir kesme noktası ve hata ayıklayıcı uygulamanızın anlık görüntüsünü alır. Kaydedilen anlık görüntü, önceki kesme noktaları veya adımlara geri dönün ve daha önce olduğu gibi uygulama durumunu görüntülemek etkinleştirin. IntelliTrace geri adım atma önceki uygulama durumu görmek istiyorsanız ancak hata ayıklamayı yeniden başlatın veya istenen uygulama durumu yeniden istemediğiniz durumlarda size zaman kazandırabilir.

Gidin ve anlık görüntüleri kullanarak görüntüle **adım geriye dönük** ve **İleri** hata ayıklama araç çubuğu düğmeleri. Bu düğmeler görünen olaylar gidin **olayları** sekmesinde **tanılama araçları** penceresi.

![Geri ve İleri düğmelerini adım](../debugger/media/intellitrace-step-back-icons-description.png  "adım geri ve İleri düğmelerini")

Daha fazla bilgi için [IntelliTrace kullanarak önceki uygulama durumlarını İnceleme](../debugger/view-historical-application-state.md) sayfası.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, birçok hata ayıklayıcı özelliklerine Hızlı Bakış vardı. Bir örnek uygulaması kullanarak bu özellikleri daha derinlemesine göz isteyebilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio kullanarak hata ayıklamayı öğrenin](../debugger/getting-started-with-the-debugger.md)
