---
title: Python kodu ölçü performansı
description: CPython tabanlı yorumlayıcılarını kullanırken Python kodunda hata ayıklama performansını denetlemek için Visual Studio profil oluşturucu kullanın.
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
ms.openlocfilehash: 931bbcea67d8595ec171ef7e08756aa5b84cc2e4
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53062945"
---
# <a name="profile-python-code"></a>Profil Python kodu

CPython tabanlı yorumlayıcılarını kullanırken bir Python uygulaması profilini oluşturabilirsiniz. (Bkz [matris özellikler - profil oluşturma](overview-of-python-tools-for-visual-studio.md#matrix-profiling) Visual Studio'nun farklı sürümleri için bu özelliğin kullanılabilirliği için.)

## <a name="profiling-for-cpython-based-interpreters"></a>CPython tabanlı yorumlayıcılarını için profil oluşturma

Profil oluşturma ile başlatıldığından **Çözümle** > **Python profil oluşturmayı Başlat** menü komutu, bir yapılandırma iletişim kutusunu açar:

![Profil oluşturma yapılandırma iletişim kutusu](media/profiling-start.png)

Seçtiğinizde, **Tamam**, profil oluşturucu çalıştırır ve üzerinden araştırmak için izleyebileceğiniz uygulama harcanan süre nasıl bir performans raporu açar:

![Profil oluşturma performans raporu](media/profiling-results.png)

|   |   |
|---|---|
| ![video kamera simgesini film](../install/media/video-icon.png "bir video izleyin") | [(Microsoft Virtual Academy) videoyu](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Profiling-Python-s6FoC6LWE_1005918567) (3 m 00s) profil oluşturma Python tanıtımı için.|

> [!Note]
> Şu an tam uygulama profili oluşturma, bu düzeyi yalnızca Visual Studio destekler, ancak kesinlikle gelecekteki özellikleriyle ilgili Geri bildirimlerinizi merak ediyoruz. Kullanım [ **ürün geri bildirimi** düğmesi](#feedback) bu sayfanın alt kısmındaki.

## <a name="profiling-for-ironpython"></a>IronPython için profil oluşturma

IronPython CPython tabanlı bir yorumlayıcı olmadığı için yukarıdaki profil oluşturma özelliğini çalışmaz.

Bunun yerine, Visual Studio .NET profil oluşturucuyu başlatıp kullanın *ipy.exe* doğrudan hedef uygulama, başlangıç betiği başlatmak için uygun bağımsız değişkenleri kullanarak. Dahil `-X:Debug` tüm Python emin olmak için komut satırında kod hata ayıklama profili ve. Bu bağımsız değişken, IronPython çalışma zamanı ve kodunuzu harcanan süre de dahil olmak üzere bir performans raporu oluşturur. Kodunuzu karıştırılmış adları kullanılarak tanımlanır.

Alternatif olarak, IronPython bazı kendi yerleşik profil vardır ancak şu anda bunun için hiçbir iyi Görselleştirici yoktur. Bkz: [bir IronPython Profiler](https://blogs.msdn.microsoft.com/curth/2009/03/30/an-ironpython-profiler/) (MSDN bloglarında) için kullanılabilir.
