---
title: Visual Studio Test Professional iş yükü ve bileşen kimlikleri
titleSuffix: ''
description: Visual Studio iş yükünü ve bileşen kimliklerini kullanarak generaldıst test ediciler için tümleşik test araçları sağlayın
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.date: 03/16/2020
ms.topic: reference
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.assetid: 70c03438-8434-4921-ada0-c172519af431
ms.prod: visual-studio-windows
ms.technology: vs-installation
monikerRange: vs-2017
open_to_public_contributors: false
ms.openlocfilehash: ee8d3d91f5079e23d5a0342c58b2db5a70e45f64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99886476"
---
# <a name="visual-studio-test-professional-component-directory"></a>Visual Studio Test Professional bileşen dizini

Bu sayfadaki tablolarda, komut satırını kullanarak Visual Studio 'Yu yüklemek için kullanabileceğiniz veya bir VSıX bildiriminde bağımlılık olarak belirtebileceğiniz kimlikler listelenmektedir. Visual Studio 'Da güncelleştirmeler yayınlıyoruz, ek bileşenler ekleyeceğiz.

Ayrıca, sayfa hakkında aşağıdakilere de göz önünde bulabilirsiniz:

* Her iş yükü kendi bölümüne sahiptir ve iş yükü KIMLIĞI ve iş yükü için kullanılabilir bileşenlerin bir tablosu gelir.
* Varsayılan olarak, **gerekli** bileşenler iş yükünü yüklediğinizde yüklenir.
* Seçeneğini belirlerseniz, **Önerilen** ve **isteğe bağlı** bileşenleri de yükleyebilirsiniz.
* Ayrıca, herhangi bir iş yükü ile bağlantılı olmayan ek bileşenleri listeleyen bir bölüm ekledik.

VSıX bildiriminizde bağımlılıklar ayarladığınızda, yalnızca bileşen kimliklerini belirtmeniz gerekir. En düşük bileşen bağımlılıklarımızı öğrenmek için bu sayfadaki tabloları kullanın. Bazı senaryolarda bu, bir iş yüküyle yalnızca bir bileşen belirttiğinizde anlamına gelebilir. Diğer senaryolarda, tek bir iş yüküyle birden çok bileşeni veya birden çok iş yükünün birden çok bileşenini belirtmeniz anlamına gelebilir. Daha fazla bilgi için bkz. [nasıl yapılır: genişletilebilirlik projelerini Visual Studio 'Ya geçirme 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md) sayfası.

Bu kimlikleri kullanma hakkında daha fazla bilgi için bkz. [Command-Line parametrelerini kullanarak Visual Studio 2017 sayfasını yüklemek](use-command-line-parameters-to-install-visual-studio.md) . Ayrıca, diğer ürünlerin iş yükü ve bileşen kimliklerinin bir listesi için bkz. [Visual Studio 2017 Iş yükü ve bileşen kimlikleri](workload-and-component-ids.md) sayfası.

## <a name="test-professional"></a>Test Uzmanı

**Kimliği:** Microsoft. VisualStudio. Workload. TestProfessional

**Açıklama:** Test Professional, kendi test yaşam döngüsünün tamamında test ihtiyaçlarını kullanmalarına yardımcı olan, genel test ediciler için hedeflenen tümleşik test araçları sağlar.

### <a name="components-included-by-this-workload"></a>Bu iş yükünün içerdiği bileşenler

Bileşen KIMLIĞI | Name | Sürüm | Bağımlılık türü
--- | --- | --- | ---
Microsoft. VisualStudio. Component. TestTools. FeedbackClient | Microsoft Geri Bildirim İstemcisi | 15.6.27406.0 | Gerekli
Microsoft. VisualStudio. Component. TestTools. MicrosoftTestManager | Microsoft Test Manager | 15.6.27406.0 | Gerekli

## <a name="unaffiliated-components"></a>Bağlantılı olmayan bileşenler

Bunlar herhangi bir iş yüküne dahil olmayan, ancak tek bir bileşen olarak seçilebilir olan bileşenlerdir.

Bileşen KIMLIĞI | Name | Sürüm
--- | --- | ---
yok | yok | yok

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio iş yükü ve bileşen kimlikleri](workload-and-component-ids.md)
* [Visual Studio yönetici kılavuzu](visual-studio-administrator-guide.md)
* [Komut satırı parametrelerini kullanarak Visual Studio'yu yükleme](use-command-line-parameters-to-install-visual-studio.md)
  * [Komut satırı parametresi örnekleri](command-line-parameter-examples.md)
* [Visual Studio’nun çevrimdışı yüklemesini oluşturma](create-an-offline-installation-of-visual-studio.md)
