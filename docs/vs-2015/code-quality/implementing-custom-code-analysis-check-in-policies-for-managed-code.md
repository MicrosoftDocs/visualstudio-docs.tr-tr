---
title: Yönetilen kod için özel kod çözümleme iade ilkelerini uygulama | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.code.analysis.selecttfsrulesets
- vs.code.analysis.browsefortfsruleset
- vs.code.analysis.policyeditor
ms.assetid: fd029003-5671-4b24-8b6f-032e0a98b2e8
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 82f360bb9dc256fd78a8b06aca66d9e49c57ab22
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49268976"
---
# <a name="implementing-custom-code-analysis-check-in-policies-for-managed-code"></a>Yönetilen Kod için Özel Kod Çözümleme İade İlkelerini Uygulama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi iade ilkesi sürüm denetimine iade edilmeden önce bir takım projesinin üyeleri kaynak kodunu çalıştırmanız gereken kurallar kümesini belirtir. Microsoft, standart bir dizi sağlar *kural kümeleri* bu grubu Kod Analizi kuralları işlevsel alanlara. *Özel iade ilke kural kümelerinin* belirli bir takım projesi için Kod Analizi kuralları kümesi belirtin. Bir kural kümesi bir .ruleset dosyası depolanır.  
  
 İade ilkeleri takım projesi düzeyinde belirlenir ve sürüm denetimi ağacındaki bir .ruleset dosyası konumunu tarafından belirtilen. Takım ilke özel kural kümesi sürüm denetimi konumunu ilgili bir kısıtlama yoktur.  
  
 Kod Analizi her proje için Özellikler penceresindeki bireysel kod projeleri için yapılandırılır. Bir kod projesi için özel bir kural .ruleset dosyası yerel bilgisayardaki fiziksel konumunu belirtilir. Kod projesini aynı sürücüde bulunan bir .ruleset dosyası belirtildiğinde, Visual Studio Proje yapılandırma dosyasına göreli bir yol kullanır.  
  
 Takım projesi özel kural kümesi oluşturmak için önerilen bir yöntem, herhangi bir kod projesinin bir parçası değil özel bir klasöre iade ilkesi .ruleset dosyası depolamaktır. Adanmış bir klasörde dosya depolama, kural dosyası düzenleyebilen kısıtlayan izinler uygulayabilirsiniz ve dizin yapısı kolayca taşıyabilirsiniz, proje başka bir dizin ya da bilgisayar içeriyor.  
  
## <a name="creating-the-team-project-custom-check-in-rule-set"></a>Takım projesi iade özel kural kümesi oluşturma  
 Bir takım projesi için özel bir kural oluşturmak için önce kümesinde iade ilkesi kuralı için özel bir klasör oluşturun **Kaynak Denetim Gezgini**. Ardından, kural kümesi dosyası oluşturun ve dosyayı sürüm denetimine ekleyin. Son olarak, kural olarak kod çözümleme iade ilkesi takım projesi için kümesi belirtin.  
  
> [!NOTE]
>  Bir takım projesinde bir klasör oluşturmak için önce takım projesi kök yerel bilgisayardaki bir konuma eşlemeniz gerekir. Daha fazla bilgi için [oluşturma ve çalışma alanları (eski) ile çalışma](http://msdn.microsoft.com/en-us/db4d5692-179a-44fe-ad31-0c1c900c9cb2).  
  
#### <a name="to-create-the-version-control-folder-for-the-check-in-policy-rule-set"></a>Sürüm denetimi klasörü İade İlkesi kural kümesi oluşturmak için  
  
1.  İçinde [!INCLUDE[esprtfc](../includes/esprtfc-md.md)]ekip projesi düğümünü genişletin ve ardından **kaynak denetimi**.  
  
2.  İçinde **klasörleri** bölmesinde, takım projesine sağ tıklayın ve ardından **yeni klasör**.  
  
3.  Ana Kaynak Denetim Masası'nda, sağ **yeni klasör**, tıklayın **Yeniden Adlandır**, klasör kural kümesi için bir ad yazın.  
  
#### <a name="to-create-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesi oluşturmak için  
  
1.  Üzerinde **dosya** menüsünde **yeni**ve ardından **dosya**.  
  
2.  İçinde **kategorileri** listesinde **genel**.  
  
3.  İçinde **şablonları** listesinde, çift **Kod Analizi kural kümesi**.  
  
4.  Kural kümesinden dahil edilecek kuralları belirtin ve sonra kural kümesi dosyası oluşturduğunuz kural kümesi klasörüne kaydedin.  
  
     Daha fazla bilgi için [özel kural kümeleri oluşturma](../code-quality/creating-custom-code-analysis-rule-sets.md)  
  
#### <a name="to-add-the-rule-set-file-to-version-control"></a>Kural eklemek için dosya sürüm denetimi için ayarlama  
  
1.  İçinde **Kaynak Denetim Gezgini**yeni klasörü sağ tıklatın ve ardından **öğeleri klasöre Ekle**.  
  
     Daha fazla bilgi için [sürüm denetimi kullanın](http://msdn.microsoft.com/library/33267cee-fe5f-4aa3-b2cd-6d22ceace314).  
  
2.  Kural kümesi oluşturduğunuz dosya tıklayın ve ardından **son**.  
  
     Dosya kaynak denetimine eklediğiniz ve sizin için kullanıma.  
  
3.  İçinde **Kaynak Denetim Gezgini** Ayrıntıları penceresi, dosya adına sağ tıklayın ve ardından **bekleyen değişiklikleri iade et**.  
  
4.  İçinde **iade** iletişim kutusu, bir açıklama ekleyin ve ardından seçeneğine sahip **iade**.  
  
    > [!NOTE]
    >  Takım projeniz için Kod Analizi İlkesi iade zaten yapılandırdıysanız ve seçtiğiniz **yalnızca geçerli çözümün bir parçası olan dosyaları içerecek şekilde iade zorunlu**, bir ilke hatası uyarısı tetikler. İlke hatası iletişim kutusunda **ilke hatası geçersiz kıl ve iade etmeye devam et**. Gerekli bir açıklama ekleyin ve ardından **Tamam**.  
  
#### <a name="to-specify-the-rule-set-file-as-the-check-in-policy"></a>Dosyası kural belirtmek için iade ilke olarak ayarlayın  
  
1.  Üzerinde **takım** menüsünde **takım projesi ayarları**ve ardından **kaynak denetimi**.  
  
2.  Tıklayın **iade ilkesi**ve ardından **Ekle**.  
  
3.  İçinde **iade ilkesi** listesinde, çift **Kod Analizi**, emin olun **yönetilen kod için kod analizini zorla** onay kutusu seçilidir.  
  
4.  İçinde **bu kural kümesini Çalıştır** listesinde  **\<kaynak denetiminden kural kümesi seçin >**.  
  
5.  Sürüm denetimine iade ilkesi kural kümesi dosyası yolunu yazın.  
  
     Yol aşağıdaki sözdizimine uygun olmalıdır:  
  
     **$/** `TeamProjectName` **/** `VersionControlPath`  
  
    > [!NOTE]
    >  Yolu aşağıdaki yordamlardan birini kullanarak kopyalayabilirsiniz **Kaynak Denetim Gezgini**:  
  
    -   İçinde **klasörleri** bölmesinde, kural kümesi dosyası içeren klasörü tıklatın. Görünen klasörün sürüm denetim yolu Kopyala **kaynak** kutusuna ve kural kümesi dosyası adını elle yazın.  
  
    -   Kural kümesi dosyası Ayrıntıları penceresinde sağ tıklayın ve ardından **özellikleri**. Üzerinde **genel** sekmesinde, bu değeri kopyalayın **sunucu adı**.  
  
## <a name="synchronizing-code-projects-to-the-check-in-policy-rule-set"></a>İade İlkesi kural kümesi için kod projelerini eşitleme  
 Belirttiğiniz bir takım projesi iade ilkesi kuralı Özellikler iletişim kutusunda kod projesinin kod proje yapılandırmasının Kod Analizi kural kümesi olarak ayarlayın. Kural kümesi kod projesini aynı sürücüde yer alıyorsa, göreli bir yol kural kümesi yolu dosya iletişim kutusundan seçildiğinde belirtmek için kullanılır. Denetim yapıları benzer yerel sürüm kullanan diğer bilgisayarlar için taşınabilir proje özellikleri ayarlar göreli bir yol sağlar.  
  
#### <a name="to-specify-a-team-project-rule-set-as-the-rule-set-of-a-code-project"></a>Bir takım projesi kural belirtmek için bir kod proje kural kümesi olarak ayarlayın.  
  
1.  Gerekirse, iade ilkesi kuralı kümesi klasör ve dosya sürüm denetiminden alın.  
  
     Bu adımda gerçekleştirdiğiniz **Kaynak Denetim Gezgini** sağ tıklayarak kural klasörünü ve ardından kümesi **en son sürümü Al**.  
  
2.  İçinde **Çözüm Gezgini**kod projesine sağ tıklayın ve ardından **özellikleri**.  
  
3.  **Kod Analizi tıklayın**.  
  
4.  Gerekirse, uygun seçenekleri tıklayın **yapılandırma** ve **Platform** listeler.  
  
5.  Kod Analizi proje kodu belirtilen yapılandırma kullanılarak oluşturulan her tamamlanışında çalıştırılacak seçin **etkinleştir (code_analysıs sabitini tanımlar) derlemede kod analizini** onay kutusu.  
  
6.  Diğer şirketlerin bileşenleri kodda yoksaymak için seçin **üretilen koddan gelen sonuçları Gizle** onay kutusu.  
  
7.  İçinde **bu kural kümesini Çalıştır** listesinde  **\<Gözat … >**.  
  
8.  İade İlkesi kural kümesi dosyası yerel sürümünü belirtin.



