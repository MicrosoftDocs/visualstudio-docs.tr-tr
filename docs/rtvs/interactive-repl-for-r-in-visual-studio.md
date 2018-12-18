---
title: R etkileşimli REPL
description: Etkileşimli REPL ortamı için Düzenleyicisi windows ile tümleşik R çözümdeki Studio nasıl kullanıldığını.
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a9e475e108fee9134699b0ee80e59fbf3f5eea32
ms.sourcegitcommit: f685fa5e2df9dc307bf1230dd9dc3288aaa408b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238454"
---
# <a name="work-with-the-r-interactive-window"></a>R etkileşimli penceresiyle çalışma

R araçları için Visual Studio (RTVS) sağlayan bir R etkileşimli pencere olarak da bilinen bir **REPL** (Read-değerlendir-yazdırma-döngüsü) penceresinde, R kodu girin ve hemen sonuçlarını görebilirsiniz. Tüm modülleri, sözdizimi ve değişkenleri yanı IntelliSense, kullanılabilir etkileşimli pencerede.

Etkileşimli penceresi de normal R Düzenleyicisi windows ile tümleşiktir. Kod ve tuşuna seçebileceğiniz **Ctrl**+**Enter**, veya sağ tıklatın ve seçin **etkileşimli Execute**, ve kod satırı satırı çalıştırılır etkileşimli ' Pencere sanki doğrudan belirtilmiş. İmleç bir Düzenleyicisi penceresinde, tek bir satırda olduğunda **Ctrl**+**Enter** bu satırı etkileşimli penceresine gönderir ve ardından bir sonraki satıra imleci taşır. Yalnızca basabilirsiniz bu şekilde **Ctrl**+**Enter** art arda kodlarda adıma.

Bu özellikler yaşamaya izleyin [R ile çalışmaya başlama](getting-started-with-r.md) izlenecek yanı sıra bu makaledeki bölümler. [Kod parçacıkları](code-snippets-for-r.md) R Düzenleyici pencerelerinde yaptığınız gibi etkileşimli penceresinde de çalışır.

## <a name="overview-of-the-interactive-window"></a>Etkileşimli pencere genel bakış

Geçerli R kod yazıp ENTER tuşuna basarak **Enter** satırın sonunda kodu söz konusu satıra çalışır:

```repl
> 3 + 3
[1] 6
```

Tuşuna basarak **Enter** herhangi bir yerde tek satırlı giriş, o satırdaki de çalışır.

Önceki tüm giriş ve çıkış REPL salt okunurdur ve değiştirilemez. Ancak, seçin ve herhangi bir zamanda penceresinden metin yanı sıra yapıştırılan kopyalayın. Satır girilmiş gibi yapıştırılan kodu çalıştırır.

Diğer bir deyişle, bir ifade ve tuşuna yazarak başlattığınızda **Enter**, RTVS zaman devam deyim bilir ve çok satırlı moduyla girer + sol ve uygun girinti sor. RTVS de parantez, köşeli ayraçlar ve süslü ayraçlar gerçekleştirir:

![Etkileşimli penceresindeki çok satırlı deyimi girişine](media/repl-multiline-entry.png)

Bu çok satırlı modda **Enter** anahtarı, aksi takdirde, yeni bir satır ekler bloğun sonunda getirildiğinde, yalnızca kod bloğu çalıştırır. Ancak, basabilirsiniz **Ctrl**+**Enter** bu kodu çalıştırmak için herhangi bir konumda hemen engelleyin.

### <a name="toolbar-commands"></a>Araç çubuğu komutları

Kendi araç etkileşimli penceresiyle şöyledir:

![Araç çubuğu ile etkileşimli penceresi](media/repl-window.png)

Araç çubuğu komutlarını aşağıdaki gibidir, hangi çoğu klavye eşdeğerleri ve üzerinde de kullanılabilir **R Araçları** > **oturum** ve **R Araçları**  >  **Çalışma dizini** menüler (veya bir belirtildiği gibi):

| Düğme | Komut | Tuş bileşimini | Açıklama | 
| --- | --- | --- | --- |
| ![Sıfırla düğmesi](media/repl-toolbar-01-reset.png) | Sıfırla | **CTRL**+**Shift**+**F10** | Tüm değişkenleri ve Geçmiş temizleme etkileşimli window oturumu sıfırlar. |
| ![Boş düğme](media/repl-toolbar-02-clear.png) | Temizle | **CTRL**+**m** | Etkileşimli penceresinde gösterilen çıkış temizler; oturum değişkenleri veya geçmiş etkilemez. |
| ![Geçmişi düğmeleri](media/repl-toolbar-03-history.png) | Önceki geçmişi komutu<br/>Sonraki geçmişi komutu | **Yukarı**, **aşağı**<br/>**Alt**+**yukarı**, **Alt**+**aşağı** | Çok satırlı kod blokları için belirli davranışları ile geçmişinde kaydırır. Bkz: [geçmişi](#history). |
| ![Yük çalışma düğmesi](media/repl-toolbar-04-load-workspace.png) | Yük çalışma | yok | Bir önceki çalışma kaydedilen yükler (bkz [çalışma alanları ve oturumlar](#workspaces-and-sessions). |
| ![Çalışma alanı Farklı Kaydet düğmesi](media/repl-toolbar-05-save-workspace-as.png)| Çalışma alanı olarak Kaydet | yok | Bir çalışma alanı olarak oturumun geçerli durumunu kaydeder (bkz [çalışma alanları ve oturumlar](#workspaces-and-sessions). |
| ![Kaynak R betiği düğmesi](media/repl-toolbar-06-source-r-script.png) | Kaynak R betiği | **CTRL**+**Shift**+**S** | Çağrıları `source` Visual Studio düzenleyicisinde şu anda etkin R betiği ile çalıştığı kodu.  Bu düğme, yalnızca bir R dosyasını Visual Studio düzenleyicisinde açık olduğunda görüntülenir. | 
| ![Kaynak R betiği Yankı düğmesi](media/repl-toolbar-07-source-r-script-with-echo.png) | Echo kaynak R betiği | **CTRL**+**Shift**+**girin** | Kaynak R betiği aynı ancak betiğin içeriği etkileşimli pencerede görüntülenir. |
| ![R düğmesi kesme](media/repl-toolbar-08-interrupt-r.png)| Kesme R | **ESC** | Etkileşimli penceresinde çalışan kod gibi durdurur `while` ekran döngüde bu bölümün başında gösterir. |
| ![Hata ayıklayıcı düğme ekleme](media/repl-toolbar-09b-attach-debugger.png)| Hata ayıklayıcıyı Ekle | yok | Ayrıca kullanılabilir kullanarak **hata ayıklama** > **Attach R etkileşimli** komutu. | 
| ![Kaynak dosya konumu düğmesine kümesi çalışma dizini](media/repl-toolbar-10-set-working-directory-source.png)| Kaynak dosya konumu dizinine çalışma kümesi | **CTRL**+**Shift**+**E** | En son kaynaklı dosya çalışma dizinine yüklenen etkileşimli penceresine kümeleri (kullanarak `source`). Bkz: [çalışma dizini](#working-directory). |
| ![Proje konumu düğmesi için çalışma dizini ayarlayın](media/repl-toolbar-11-set-working-directory-to-project.png) | Çalışma dizini proje konumuna ayarlayın | **CTRL**+**Shift**+**P** | Visual Studio şu anda yüklenen proje kökündeki için çalışma dizini ayarlar. Bkz: [çalışma dizini](#working-directory). |
| (Metin alanı) | Çalışma seçin dizini | yok | Çalışma dizini için doğrudan giriş alanı. Bkz: [çalışma dizini](#working-directory). |

## <a name="workspaces-and-sessions"></a>Çalışma alanları ve oturumlar

Etkileşimli penceresinde kod çalıştıran bir bağlamı Geçerli oturumunuzda oluşturur. Bağlam genel değişkenler, işlev tanımları, kitaplık yükler ve benzeri oluşur. Bu bağlamda topluca adlı bir *çalışma*, kaydedin ve herhangi bir zamanda çalışma alanları yük. 

Seçme **çalışma Kaydet** düğmesini veya kullanarak **R Araçları** > **oturum** > **çalışma Kaydet**komut sizden bir konum ve dosya adı için (varsayılan uzantısı *. RData*).

Belirli bir dosya adı kullanarak bir çalışma alanı kaydetmek için (varsayılan *. RData*), tıklayın **çalışma alanını Kaydet** REPL düğmesini:

Daha önce kaydedilmiş bir çalışma alanı yeniden yüklemeyi seçin **yük çalışma** düğmesini tıklatın veya kullanmak **R Araçları** > **oturum** > **yükleme Çalışma alanı** ve çalışma alanı dosyasına gidin.

**Sıfırlama** düğmesini veya **R Araçları** > **oturum** > **sıfırlama** oturum bağlamı temizler. Bir uzak oturum kullanıyorsanız, sıfırlama depolanan tüm dosyaları temizlemek için uzak makinede kullanıcı profili de siler. (Bkz [çalışma alanları](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Çalışma dizini

Geliştiriciler genellikle kendi çalışma dizini sırada etkileşimli bir oturumda değiştirmek istiyorum. Araç çubuğunda, kullanılabilen çeşitli komutları **R Araçları** > **çalışma dizini** menü ve proje bağlam menüsünde bir çalışma dizini kaynak dosyası konumuna kolayca ayarlamanıza izin verir , konumu veya projenizi veya herhangi bir rastgele konumu. Bunun yapılması, dosyalar için söz konusu olduğunda tam yol adları veya uzun göreli yol adlarını yazarak önlemenize yardımcı olur.

## <a name="history"></a>Geçmiş

Etkileşimli penceresinde girin her satır bir Düzenleyicisi'nden gönderilen satırları içerir, çoğaltma'nın geçmişi korunur. Komut satırında olasılıkla alışkın için olduğu gibi sonra Yukarı ve aşağı ok tuşlarına geçmişinde gidebilirsiniz.

Geçerli satırda yazmaya başlayın ve tuşuna basın, geçerli satır içinde korunur geçmişinizi bile aracılığıyla henüz çalıştırmanızı bu satırı henüz bir farktır.

Etkileşimli pencere geçmişinde akıllıca satırları yayılan bilgilerinin diğer kod bloğu ile de çalışır. Geçmiş yukarı ve aşağı ok tuşları dolaşma, çok satırlı kod blokları tam bir birim olarak alınır ve geçerli girişi olarak gösterilir. Bu noktada, üst veya alt ulaşılana kadar ok tuşları, kod bloğunun satır gidin. Kod bloğu üst kısmında, Yukarı Ok geçmişinde önceki öğeyi alır; alt satırında aşağı oka sonraki öğeyi alır.

Bu davranış bir yukarı ok geçmişindeki son öğeyi yeniden çalıştırma, genellikle bu durum düzenler ve **Enter** tuş vuruşu verirken doğal olarak yukarı ok tuşlarına basarak çok satırlı kod bloğunu düzenleme için birleşimi uygulamasına gidin.

Çok satırlı kod bloklarda gezinme önlemek için araç çubuğu düğmelerini kullanın veya **Alt**+**yukarı** ve **Alt**-**Aşağı**, ve tüm blokları tek bir satır olarak kabul edilir.

Geçmiş özellikleri deneyimi yapmanın en kolay yolu bunları kendiniz için etkileşimli pencerede çalışmaktır. Aşağıdaki kodu birkaç uygun tek ve birden çok satırı deyimleri sağlar. Kopyala-yapıştır her deyimiyle ayrı ayrı, ancak uygun geçmişi oluşturmak için kullanın. (Ayrıca kodu ayrı kod dosyasına yapıştırın ve etkileşimli penceresiyle satırları göndermek **Ctrl**+**Enter**.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```