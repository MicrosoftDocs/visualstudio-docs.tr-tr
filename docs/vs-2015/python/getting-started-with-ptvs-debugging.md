---
title: 'PTVS kullanmaya Başlarken: hata ayıklama | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-python
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 8a92eb3779abf5be00f39bd4aa3e66238a729ded
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204951"
---
# <a name="getting-started-with-ptvs-debugging"></a>PTVS Kullanmaya Başlarken: Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio'nun etkileşimli hata ayıklayıcısında Python kodunuzdaki sorunları tanılamak ve gidermek daha kolay hale getirir.  
  
 Bu çok kısa yönergeleri izleyebilirsiniz [youtube video](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
 Önceki alınırken başlangıç konusunda, boş bir Python uygulaması projesi oluşturun ve PythonApplication1.py aşağıdaki kodu girildi:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Normalde Visual Studio'da kod üzerinde çalışırken, F5 tuşuna basarak kodunuzu çalıştıran başlayacağız.  Bu komut tüm bölümleri oluşturulması gereken projenizin oluşturur ve hata ayıklayıcısı altında kod çalışmaya başlar.  Derleme ve hata ayıklayıcı olmadan kodunuzu başlatmak için Ctrl + F5 tuşlarına basabilirsiniz.  Hata ayıklayıcı kodunuz biraz daha yavaş çalışır, ancak harika hata ayıklama özellikleri, maliyeti alın.  
  
 Kodunuzu başlatmak için başka bir adım olarak komutu (normalde için F11 bağlı) yoludur.  F5'e olan, ancak her deyimi yürütmeyi duraklatır.  Programın belirli bir noktada kesmek istiyorsanız, bir kesme noktası ayarlamak için kod düzenleyicinin sol kenar boşluğunda sol işaretçi düğmesine basabilirsiniz.  F5 tuşuna bastığınızda, program yürütme sonu veya satırında bir kesme noktası ile durdurun.  Hata ayıklama menüsüne Adımlama seçenekleri; yine de sahip istiyor musunuz? Örneğin, adım üzerinden adımla (F11), işlev çağrıları işlev çağrıları (F10) veya bir işlev (shift-F11) sonunda atlayabilirsiniz.  
  
 Daha fazla hata ayıklayıcıda bozuk olduğunda yapabileceğiniz yoktur.  Yerel değişkenlerin geçerli değerleri Yereller penceresinde gösterir.  Kodunuzu adım olarak, yerel öğeler ekranın otomatik olarak güncelleştirir.  Yürütme durduğu değişkenleri geçerli satırına yakın gösteren otomatik değişkenler penceresi.  Hata ayıklayıcıyı otomatik olarak güncelleştirecektir herhangi bir Python ifade yazabilirsiniz İzleme penceresinde her zaman yürütmeyi durdurur.  İşaretçi de açılan bir değişken değerleri görüntüsünü görmek için düzenleyici pencerelerini değişkenlerinde üzerine gelerek ve nesneleri incelemek bu veri ipucu görüntü sağlar.  Bazı veri türleri veri ipucu görüntüleme (HTML, XML veya JSON gibi özel biçimlendirme ile Örneğin, dizeleri) erişilebilen özel görselleştiriciler sahiptir.  
  
 Geçerli deyim için hata ayıklayıcı durduğu götüren bekleyen işlev çağrıları çağrı yığını penceresini gösterir.  Burada kod her işlev yürütmeye devam, değişkenlerin değerleri arayın ve benzeri atlamak için farklı yığın çerçevesi (çağrı yığınını çizgilerle) seçebilirsiniz.  
  
 Bu çok kısa yönergeleri izleyebilirsiniz [youtube video](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTVS kullanmaya başlama ve kapsamlı videolar alma](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)

