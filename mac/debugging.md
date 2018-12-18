---
title: Xamarin ile hata ayıklama
description: Hata ayıklama, programlama, ortak ve gerekli bir parçasıdır. Olgun bir IDE Mac için Visual Studio kolay hata ayıklama yapmak için özellikleri içeren tam bir paketi içerir. Güvenli, veri görselleştirme için hata ayıklamasından bu makalede Mac için Visual Studio'da hata ayıklama tam potansiyelini kullanmayı açıklar
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.technology: vs-ide-debug
ms.assetid: BB7A084D-9AC2-48B5-8076-6C8518796BBA
ms.openlocfilehash: e17a423e9db6826c8cc693e1c75c75bb067a19e8
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51295299"
---
# <a name="debugging-with-xamarin"></a>Xamarin ile hata ayıklama

Mac için Visual Studio yerel hata ayıklayıcı bir izin verme hata ayıklama desteği Xamarin.iOS ve Xamarin.Mac Xamarin.Android uygulamaları için sahiptir.

Kullandığı Mac için Visual Studio [ *Mono geçici hata ayıklayıcı*](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger/), tüm platformlardaki yönetilen kodda hata ayıklamak Mac için Visual Studio izin vererek Mono çalışma zamanı içinde uygulanır.

## <a name="the-debugger"></a>Hata ayıklayıcı

Visual Studio hata ayıklamak için Mono geçici hata ayıklayıcı Mac kullanan yönetilen (C# veya F#) tüm Xamarin uygulamaları kod. Mono geçici hata ayıklayıcı farklıdır; Mono çalışma zamanına yerleşik birlikte operative bir hata ayıklayıcı olması normal hata ayıklayıcıları oluşturulan kodun ve Mono çalışma zamanı hata ayıklama deneyimini sağlamak için IDE ile birlikte çalışır. Mono çalışma zamanı daha fazla bilgi edinebilirsiniz kablo protokolü aracılığıyla hata ayıklama işlevselliği kullanıma sunan [Mono belgelerinde](http://www.mono-project.com/docs/advanced/runtime/docs/soft-debugger-wire-format/).

Sabit hata ayıklayıcıları gibi [LLDB]( http://lldb.llvm.org/index.html) veya [GDB]( https://www.gnu.org/software/gdb/), bilgi veya hata ayıklanan programın işbirliği olmadan bir programı denetleme, ancak yine de olay Xamarin uygulamalarında hata ayıklama sırasında yararlı olabilir, Yerel iOS veya Android kod hatalarını ayıklamak gerekir.

## <a name="using-the-debugger"></a>Hata ayıklayıcıyı kullanma

Herhangi bir uygulamanın hatalarını ayıklamaya başlamak için her zaman yapılandırma emin olun **hata ayıklama**. Hata ayıklama yapılandırması yararlı birtakım Araçlar, kesme noktaları gibi hata ayıklama, görselleştiriciler verileri kullanarak ve çağrı yığınını görüntüleme desteği sağlar:

![Hata ayıklama yapılandırması](media/debugging-image_0.png)

## <a name="setting-a-breakpoint"></a>Bir kesme noktası ayarlama

IDE içinde bir kesme noktası ayarlamak için düzenleyicinizi nerede kesmek istediğiniz kod satırı sayısını yanındaki kenar boşluğu alanının tıklayın:

![Kenar boşluğu kesme noktası ayarlama](media/debugging-image0.png)

Kodunuzda giderek ayarlanan kesme noktaları görüntüleyebileceğiniz **kesme noktaları paneli**:

![Kesme noktaları listesi](media/debugging-image0a.png)

## <a name="start-debugging"></a>Hata Ayıklamayı Başlat

Hata ayıklamayı başlatmak için IDE içinde bir hedef cihaz veya benzer/öykünücü'ı seçin:

![Hedef cihaz seçin](media/debugging-image1.png)

Tuşuna basarak uygulamanızı dağıtmaya **Play** düğmesini veya **Cmd + return**. Kod, bir kesme noktasına ulaştığınızda, vurgulanan sarı olur:

![Vurgu gösteriliyor kesme noktası isabet](media/debugging-image2.png)

Hata ayıklama araçları, nesneleri değerlerini incelemek için kullanılan gibi bu noktada kodunuzda olup bitenler hakkında daha fazla bilgi almak için kullanılabilir:

![Görselleştirmeler hata ayıklama](media/debugging-image3.png)

## <a name="conditional-breakpoints"></a>Koşullu kesme noktaları

Ayrıca ayarlayabilirsiniz koşullar altında bir kesme noktası ortaya dikte kuralları, bu ekleme olarak bilinen bir *koşullu kesme noktası*. Koşullu kesme noktası ayarlamak için erişim **kesme noktası Özellikler penceresi**, hangi yapılabilir iki yolla:

* Yeni bir koşullu kesme noktası eklemek için bir kesme noktası ayarlamak istediğiniz kod için satır numarası solundaki Düzenleyici kenar sağ tıklayın ve yeni kesme noktası seçin:

 ![Kesme noktası bağlam menüsü](media/debugging-image4.png)

* Varolan bir kesme noktası için bir koşul eklemek için kesme noktasına sağ tıklatın ve **kesme noktası özelliklerini**, veya **kesme noktaları paneli**, aşağıda gösterilen kesme noktasını Düzenle düğmesini seçin:

 ![Kesme noktaları panelinde mevcut kesme noktasını Düzenle](media/debugging-image5.png)

Daha sonra gerçekleşecek şekilde kesme noktası altında istediğiniz koşulun girebilirsiniz:

 ![Kesme noktası koşulları Düzenle](media/debugging-image6.png)

## <a name="stepping-through-code"></a>Kod boyunca ilerleme

Bir kesme noktasına ulaşıldığında hata ayıklama araçları program yürütme denetime yararlanmanıza olanak tanıyacak. Mac için Visual Studio, böylece çalıştırma ve kodunuz içinde adım adım dört düğme görüntülenir. Mac için Visual Studio'da, bunlar aşağıdaki gibi görünür:

 ![Kodunuz içinde adım adım için düğmeler](media/debugging-image7.png)

Dört düğme şunlardır:

*   **Play** -bu kodun sonraki kesme noktasına kadar yürütme başlar.
*   **Step Over** -Bu kod sonraki satırı yürütür. Sonraki satır bir işlev çağrısı ise, Step Over işlev yürütülür ve kodun sonraki satırında durdurur *sonra* işlevi.
*   **İçine adımla** -Bu ayrıca sonraki kod satırına yürütülür. Sonraki satır bir işlev çağrısı ise, içine adımla işlevin ilk satır, satır satır işlevi, hata ayıklamaya devam etmenize imkan sağlar durdurur. Sonraki satır bir işlev değilse, aynı Step Over olarak davranır.
*   **Step Out** -bu satıra burada geçerli işlev çağrıldı döndürür.

## <a name="debugging-monos-class-libraries"></a>Mono'nın sınıf kitaplıklarında hata ayıklama

Mono'nın sınıf kitaplıkları için kaynak kodu ile Xamarin ürünleri gönderin ve hata ayıklayıcı'dan tek adım bu şeyleri nasıl başlık altında çalışmakta olduğunuz incelemek için kullanabilirsiniz.

Bu özellik, hata ayıklama sırasında daha fazla bellek tüketir olduğundan, varsayılan olarak kapalıdır.

Bu özelliği etkinleştirmek için Gözat **Mac için Visual Studio > Tercihler > hata ayıklayıcısı** olduğundan emin olun "**yalnızca; proje kodu hatalarını ayıklama Çerçeve kodunu adımlamadan adım değil.** " seçenek **seçilmemiş**, aşağıda gösterildiği gibi:

![Framework kod seçeneğe kodlarındaki](media/debugging-image8.png)

## <a name="see-also"></a>Ayrıca bkz.

- [(Windows üzerinde) Visual Studio'da hata ayıklama](/visualstudio/debugger/)