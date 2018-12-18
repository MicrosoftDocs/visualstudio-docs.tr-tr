---
title: Python/C++ karışık mod hata ayıklaması için semboller
description: Nasıl Visual Studio tam karışık mod C++ hem de Python hata ayıklama sembolleri olanağı sağlar.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 62e3727b36e6ba3231ee12388e1be5bde40d080a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062696"
---
# <a name="install-debugging-symbols-for-python-interpreters"></a>Hata ayıklama sembolleri için Python yorumlayıcılarını yükleme

Tam hata ayıklama deneyimini sağlamak üzere [karma mod Python hata ayıklayıcısı](debugging-mixed-mode-c-cpp-python-in-visual-studio.md) Visual Studio için Python yorumlayıcısını çok sayıda iç veri yapılarını ayrıştırmak için kullanılan hata ayıklama simgeleri. İçin *python27.dll*, örneğin, karşılık gelen sembol dosyası olduğu *python27.pdb*; *python36.dll*, sembol dosyası *python36.pdb*. Yorumlayıcı'nün her sürümü, çeşitli modüller için Sembol dosyalarını da sağlar.

Visual Studio 2017 ile Python 3 ve Anaconda 3 yorumlayıcılarını kendi ilgili semboller otomatik olarak yükleyin ve Visual Studio bu sembolleri otomatik olarak bulur. Visual Studio 2015 veya önceki veya diğer yorumlayıcılarını kullanırken, sembolleri ayrı olarak karşıdan gelin ve ardından Visual Studio aracılığıyla yapmanız **Araçları** > **seçenekleri** iletişim kutusunda **hata ayıklama** > **sembolleri** sekmesi. Bu adımlar aşağıdaki bölümlerde ayrıntılı olarak açıklanmaktadır.

Karışık mod hata ayıklama oturumu başlatma sırasında sembolleri, genellikle ihtiyaç duyduğunda, visual Studio isteyebilir. Bu durumda, iki seçenek içeren bir iletişim kutusu görüntüler:

- **Açık Simge Ayarları iletişim kutusu** açılır **seçenekleri** iletişim kutusuna **hata ayıklama** > **sembolleri** sekmesi.
- **Benim için yorumlayıcıyı sembolleri Yükle** bu mevcut belgeleri sayfasında, bu durumda, belirleyin açılır **Araçları** > **seçenekleri** gidin **hata ayıklama**   >  **Sembolleri** devam etmek için sekmesinde.

    ![Karışık mod hata ayıklayıcı semboller istemi](media/mixed-mode-debugging-symbols-required.png)

## <a name="download-symbols"></a>Sembolleri yükle

- Python 3.5 ve sonraki sürümler: hata ayıklama sembolleri Python yükleyici aracılığıyla Al. Seçin **özel yükleme**seçin **sonraki** almak için **Gelişmiş Seçenekler**, kutularını seçip **hata ayıklama sembolleri Yükle** ve **indirme hata ayıklama ikililerini**:

    ![Hata ayıklama simgeleri dahil olmak üzere Python 3.x yükleyici](media/mixed-mode-debugging-symbols-installer35.png)

    Sembol dosyaları (*.pdb*) sonra kök yükleme klasöründe bulunan (bireysel modüller için Sembol dosyalar, *DLL'leri* klasörünün yanı sıra). Bu nedenle, Visual Studio bunları otomatik olarak bulur ve başka bir adım gereklidir.

- Python 3.4.x ve önceki sürümleri: semboller kullanılabilir olarak indirilebilir *.zip* dosyalarını [resmi dağıtımları](#official-distributions) veya [Enthought Kanopi](#enthought-canopy). Dosyaları gibi devam etmek için yerel bir klasöre ayıklayın indirdikten sonra bir *sembolleri* klasörün içinde Python klasör.

    > [!Important]
    > Semboller Python küçük yapılar arasında farklılık gösterir ve 32-bit ve 64-bit derlemeler arasında bu nedenle tam olarak sürümleri eşleştirmek istediğiniz. Kullanılan yorumlayıcı denetlemek için genişletin **Python ortamları** *düğüm* projenizde altında **Çözüm Gezgini** ve ortam adını not edin. Ardından geçin **Python ortamları** *penceresi* ve yükleme konumunu not edin. Ardından bu konumda bir komut penceresi açın ve başlangıç *python.exe*, tam sürümünü görüntüleyen ve 32-bit veya 64-bit olup.

- İlişkinin ActiveState Python gibi başka bir üçüncü taraf Python dağıtım: Bu dağıtım yazarları başvurun ve bunları sembolleriyle sağlamak üzere istek. WinPython, kendi bölümü için değişiklik yapmadan standart Python yorumlayıcısı içerir, karşılık gelen sürüm numarasını resmi dağıtım simgeleri kullanın.

## <a name="point-visual-studio-to-the-symbols"></a>Visual Studio sembolleri noktası

Sembolleri ayrı olarak yüklediyseniz, Visual Studio bunları haberdar olmak için aşağıdaki adımları izleyin. Python 3.5 veya sonraki bir yükleyici aracılığıyla semboller yüklü değilse, Visual Studio bunları otomatik olarak bulur.

1. Seçin **Araçları** > **seçenekleri** menü gidin **hata ayıklama** > **sembolleri**.

1. Seçin **Ekle** düğmesi (aşağıda açıklanan) araç çubuğunda, genişletilmiş burada yüklenen semboller klasörü girin (nerede olduğu *python.pdb* gibi bulunan *c:\python34\Symbols* aşağıda gösterilmiştir) seçip **Tamam**. 

    ![Karışık mod hata ayıklayıcı seçenekleri simgeleri](media/mixed-mode-debugging-symbols.png)

1. Hata ayıklama oturumu sırasında Visual Studio ayrıca kaynak dosya konumu için Python yorumlayıcısı isteyebilir. Kaynak dosyaları indirdikten, (gelen [python.org/downloads](https://www.python.org/downloads), örneğin), sonra da, doğal olarak bunları da işaret edebilir.

> [!Note]
> İletişim kutusunda gösterilen simge önbelleğe alma özellikleri, çevrimiçi bir kaynaktan gelen simgeleri yerel önbellek oluşturmak için kullanılır. Simge zaten yerel olarak mevcut olduğundan bu özellikleri ile Python yorumlayıcısı simgeleri gerekli değildir. Her iki durumda da başvurmak [belirtin, sembol ve kaynak dosyaları Visual Studio hata ayıklayıcısı](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) Ayrıntılar için.

## <a name="official-distributions"></a>Resmi dağıtımları

| Python sürümü | İndirmeler | 
| --- | --- | 
| 3.5 ve sonraki sürümler | Python yükleyici aracılığıyla sembolleri yükleyin. | 
| 3.4.4 | [32-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32-bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32-bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32-bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32-bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32-bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32-bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64-bit](https://www.python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.15 | [32-bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.15/python-2.7.15.amd64-pdb.zip) |
| 2.7.14 | [32-bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.14/python-2.7.14.amd64-pdb.zip) |
| 2.7.13 | [32-bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.13/python-2.7.13.amd64-pdb.zip) |
| 2.7.12 | [32-bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.12/python-2.7.12.amd64-pdb.zip) |
| 2.7.11 | [32-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32-bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32-bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32-bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32-bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32-bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32-bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64-bit](https://www.python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |

## <a name="enthought-canopy"></a>Enthought Kanopi

Enthought Kanopi, 1.2 sürümünden itibaren ikili dosyalar için semboller sağlar. Bunlar otomatik olarak yanı sıra dağıtım yüklenir, ancak yine de bunları daha önce açıklandığı gibi sembol yolunu içeren klasör el ile eklemeniz gerekir. Sembolleri bulunan Kanopi tipik kullanıcı başına yüklenmesi için *%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts* 64-bit sürüm için ve *%UserProfile%\AppData\Local\Enthought\ Canopy32\User\Scripts* 32-bit sürümü için.

Enthought Python dağıtım (EPD) yanı sıra Enthought Kanopi 1.1 ve önceki yorumlayıcı sembolleri sağlamaz ve bu nedenle karışık mod hata ayıklama ile uyumlu değildir.
