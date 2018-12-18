---
title: R Araçları'nı yükleme
description: Çevrimdışı yüklemeleri dahil olmak üzere Visual Studio 2015, Visual Studio 2017'de R araçları yüklemek nasıl.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 4fdf7cb791339350ff9644d0f727e3adc299add6
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220911"
---
# <a name="how-to-install-r-tools-for-visual-studio"></a>Visual Studio için R araçları yükleme

Bu makalede:

- [Visual Studio'nun desteklenen sürümleri](#supported-versions-of-visual-studio)
- [Visual Studio 2017'de RTVS yükleyin](#installing-rtvs-in-visual-studio-2017)
- [Visual Studio 2015'te RTVS yükleyin](#installing-rtvs-in-visual-studio-2015)
- [Çevrimdışı yükleme](#offline-installation-of-visual-studio-and-rtvs)

> [!Note]
> R Araçları'nı yükledikten sonra bir en iyi duruma getirilmiş veri Bilimcisi düzeni için Visual Studio'yu yapılandırma üzerinde açıklandığı isteyebileceğiniz [seçenekleri](options-for-r-tools-in-visual-studio.md) makalesi.

## <a name="supported-versions-of-visual-studio"></a>Visual Studio'nun desteklenen sürümleri

R araçları için Visual Studio (RTVS) Windows Community (ücretsiz) ile desteklenir, Professional ve Enterprise sürümleri her iki [Visual Studio 2017](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) ve [Visual Studio 2015 güncelleştirme 3 (veya üstü)](http://go.microsoft.com/fwlink/?LinkId=691129) (doğrudan indirme).

RTVS Visual Studio şu anda Mac için desteklenmiyor

Yalnızca Visual Studio, Visual Studio Test Professional ve SQL Server Management Studio gibi ürünleri ile eklenen Kabuğu varsa RTVS yüklemez. Visual Studio Shell RTVS için gerekli bileşenler eksik.

## <a name="install-rtvs-in-visual-studio-2017"></a>Visual Studio 2017'de RTVS yükleyin

1. Visual Studio Yükleyicisi'ni çalıştırın ve seçin **Değiştir** seçeneği (Ayrıntılar için bkz [değiştirme Visual Studio](../install/modify-visual-studio.md)). Henüz Visual Studio yüklü değilse [Visual Studio'yu yükleyin](../install/install-visual-studio.md). Windows 7'de, yükleyici Visual Studio 2017 sürüm göstermek için güncelleştirilir mutlaka *15.2 yapı 26430.12* veya üzeri.

1. Seçin **veri bilimi ve analitik uygulamalar** iş yükü:

    ![Veri bilimi ve analitik uygulamalar iş yükü vs2017](media/installation-data-science-workload.png)

1. İşlecin sağ tarafındaki aynı iş yükü adı altında ek seçenekleri ayarlayın. Varsayılan olarak, bu iş yükü içerir F# ve Python destekler. R için en düşük gereksinimler verilmiştir **R dili desteğini**, **R geliştirme için çalışma zamanı desteği**, ve **Microsoft R istemcisi**.

RTVS yüklenir: *% ProgramFiles (x86) %\Microsoft Visual Studio\<sürüm >\<sürümü > Visual Studio için Common7\IDE\Extensions\Microsoft\R Araçları* burada  *\<sürümü >* genellikle `2017` ve  *\<sürümü >* olduğu `Community`, `Professional`, veya `Enterprise`.

## <a name="install-rtvs-in-visual-studio-2015"></a>Visual Studio 2015'te RTVS yükleyin

Visual Studio 2015 ile İnterpret R ve R araçları ayrı olarak yüklemeniz gerekir.

### <a name="install-an-r-interpreter"></a>R yorumlayıcıyı yükleyin

RTVS R 3.2.1 sürüm 64-bit yüklenmesini gerektirir ya da daha yüksek bir veya daha fazla aşağıdaki kaynakları:

- [Microsoft R Open](https://mran.microsoft.com/download/)
- [Microsoft R istemcisi](/machine-learning-server/r-client/what-is-microsoft-r-client)
- [CRAN R](https://cran.r-project.org/bin/windows/base/)

Microsoft R Open ve CRAN R hem de birden çok yan yana sürümler için izin verin. Microsoft R Client, ancak yalnızca bir sürümünü destekler ve her zaman yüklü en son olanı kullanır.

### <a name="install-the-r-tools"></a>R Araçları'nı yükleme

Geçerli RTVS Visual Studio 2015'ten indir [ https://aka.ms/rtvs-current ](https://aka.ms/rtvs-current). RTVS Visual Studio'nun uygun bir sürümünü denetler ve henüz yapmadıysanız İnterpret R yüklemenize yardımcı olur.

> [!Note]
> Tek başına RTVS yükleyicisi, yalnızca Visual Studio 2015 ile birlikte çalışır; Visual Studio 2017 ile R desteğini yükleme [veri bilimi ve analitik uygulamalar iş yükü](#installing-rtvs-in-visual-studio-2017) daha önce açıklandığı gibi.

Visual Studio 2015 için RTVS'yi yüklenir: `%ProgramFiles(x86)%\Microsoft Visual Studio 14\Common7\IDE\Extensions\Microsoft\R Tools for Visual Studio`

## <a name="offline-installation-of-visual-studio-and-rtvs"></a>Visual Studio ve RTVS çevrimdışı yükleme

Çevrimdışı yükleme, Internet'e bağlı olmayan bilgisayarlar için uygundur:

1. Git [Visual Studio 2017'in çevrimdışı yüklemesini oluşturma](../install/create-an-offline-installation-of-visual-studio.md).

1. Visual Studio 2015 kullanıyorsanız belirleyin **2015** içindekiler tablosu üzerinde Seçici içinde.

1. Web sayfasındaki bir çevrimdışı yükleme oluşturmak için yönergeleri izleyin.

1. Visual Studio 2015 için gelen çevrimdışı RTVS yükleyiciler indirme [ https://aka.ms/rtvs-current-zip ](https://aka.ms/rtvs-current-zip) ve [ https://aka.ms/rtvs-remote-zip ](https://aka.ms/rtvs-remote-zip).

1. Visual Studio ve RTVS çevrimdışı yükleyiciler yükleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [R kullanmaya başlama](getting-started-with-r.md)
- [R araçları örnek projeleri](getting-started-samples.md)
- [R Araçları'nda Yardım](getting-started-help.md)
- [R araçları seçenekleri](options-for-r-tools-in-visual-studio.md)
- [Microsoft Machine Learning sunucusu (eski adıyla R sunucusu)](/machine-learning-server/)