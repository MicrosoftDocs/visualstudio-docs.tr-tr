---
title: Python arama yollarını nasıl uygulanır
description: Visual Studio, ortamlar ve sistem genelinde değişkenleri kullanmaktan kaçınmak için projeleri için arama yollarını belirtmek daha fazla belirli bir araçları sağlar.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e3e6bd1ce14e1803e48a476246e3cfb8858286bb
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051535"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Visual Studio, Python arama yollarını nasıl kullanır?

Tipik Python kullanımla `PYTHONPATH` ortam değişkeni (veya `IRONPYTHONPATH`, vs.) Modülü dosyaları için varsayılan arama yolu sağlar. Diğer bir deyişle, kullandığınızda bir `from <name> import...` veya `import <name>` deyimi, Python, eşleşen bir ad için sırayla aşağıdaki konumlarda arar:

1. Python'ın yerleşik modül.
1. Kullanmakta olduğunuz Python kodu içeren klasör.
1. "Geçerli bir ortam değişkeni tarafından tanımlanan modülü arama yolunu" olarak. (Bkz [modül arama yolu](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) ve [ortam değişkenlerini](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) Python belgeleri core'da.)

Visual Studio arama path ortam değişkenine bile tüm sistem için değişkeni ayarlandığında ancak yok sayar. Göz ardı edilir, aslında, tam olarak *çünkü* tüm sistem için ayarlanır ve bu nedenle otomatik olarak yanıtlanan bazı sorular başlatır: olan başvurulan modülleri Python 2.7 veya Python 3.6 + geliyordu? Standart kitaplık modülleri geçersiz olacak? Bu davranışı kullanan bir geliştiricidir yoksa bir kötü amaçlı geçirme girişimi mı?

Visual Studio, bu nedenle doğrudan hem ortamları ve projelerinde arama yollarını belirtmek için bir yol sağlar. Çalıştırın ya da Visual Studio'da hata ayıklama kodu değerini arama yollarını alır `PYTHONPATH` (ve diğer eşdeğer değişkenleri). Arama yolları ekleyerek, Visual Studio o konumlardaki kitaplıkları inceler ve IntelliSense veritabanları için gerektiğinde derler (Visual Studio 2017 sürüm 15.5 ve önceki; veritabanı oluşturmak biraz zaman alabilir kitaplıkları sayısına bağlı olarak).

Bir arama yolu eklemek için Git **Çözüm Gezgini**, proje düğümünü, sağ **arama yollarını**seçin **klasörü için arama yolu Ekle**:

![Çözüm Gezgini'nde arama yollarında arama yolu komutuna klasörü Ekle](media/search-paths-command.png)

Bu komut ardından dahil etmek için klasörü seçin, bir tarayıcı görüntüler.

Varsa, `PYTHONPATH` ortam değişkeni zaten istediğiniz klasörleri içeren, kullanın **ise PYTHONPATH eklemek için arama yollarını** kullanışlı bir kısayol olarak.

Visual Studio bu yollar klasörleri arama yollarını eklendikten sonra projeyle ilişkili her ortam için kullanır. (Hatalar ortamı Python 3'te temel alır ve Python 2.7 modülleri için bir arama yolu eklemek çalışırsanız görebilirsiniz.)

İle dosyaları bir *.zip* veya *.egg* uzantısı eklenebilir arama yolları seçerek **Zip arşivine arama yolu Ekle** komutu. Klasörlerle olduğu gibi bu dosyaların içeriğini taranan ve IntelliSense için kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Python ortamlarını yönetme](managing-python-environments-in-visual-studio.md)
- [Proje için yorumlayıcıyı seçme](selecting-a-python-environment-for-a-project.md)
- [Bağımlılıklar için Requirements.txt dosyasını kullanma](managing-required-packages-with-requirements-txt.md)
- [Python ortamları penceresi başvurusu](python-environments-window-tab-reference.md)
