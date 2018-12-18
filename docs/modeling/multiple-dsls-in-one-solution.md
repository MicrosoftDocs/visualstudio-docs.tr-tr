---
title: Bir Çözümde Birden Çok DSL
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: f73fd8170c91fe51692c9ec5b5b39e7c36570dd2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49949376"
---
# <a name="multiple-dsls-in-one-solution"></a>Bir Çözümde Birden Çok DSL
Bunlar birlikte yüklenir, böylece tek bir çözümün bir parçası birkaç DSL'ler paketleyebilirsiniz.

 Birden çok DSL tümleştirmek için çeşitli teknikler kullanabilirsiniz. Daha fazla bilgi için [Visual Studio Modelbus kullanarak modelleri tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md) ve [nasıl yapılır: sürükle ve bırak işleyicisi ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md) ve [kopyalama davranışını özelleştirme](../modeling/customizing-copy-behavior.md).

### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Aynı çözümdeki birden çok DSL oluşturmak için

1. İki veya daha fazla DSL çözümler ve bir VSIX projesi oluşturun ve tüm projeler tek bir çözüme ekleyin.

   -   Yeni bir VSIX projesi oluşturmak için: içinde **yeni proje** iletişim kutusunda **Visual C#**, **genişletilebilirlik**, **VSIX projesi**.

   -   VSIX çözüm dizininde değil iki veya daha fazla DSL çözümleri oluşturun.

        Her bir DSL için Visual Studio'nun yeni bir örneğini açın. Yeni DSL oluşturun ve VSIX çözümle aynı çözüm klasörü belirtin.

        Farklı bir dosya adı uzantısı ile her DSL oluşturduğunuzdan emin olun.

   -   Adlarını değiştirme **Dsl** ve **DslPackage** böylece tüm farklıdır projeleri. Örneğin: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.

   -   Her **DslPackage\*\source.extension.tt**, bu satırı doğru Dsl projesi adıyla güncelleştirin:

        `string dslProjectName = "Dsl2";`

   -   Dsl * ve DslPackage VSIX çözümüne ekleme\* projeleri.

        Kendi çözüm klasöründe her çifti yerleştirmek isteyebilirsiniz.

2. DSL VSIX bildirimlerini Birleştir:

   1.  Açık _YourVsixProject_**\source.extension.manifest**.

   2.  Her bir DSL seçin **İçerik Ekle** ekleyin:

       -   `Dsl*` Proje olarak bir **MEF Bileşeni**

       -   `DslPackage*` Proje olarak bir **MEF Bileşeni**

       -   `DslPackage*` Proje olarak bir **VS paket**

3. Çözümü oluşturun.

   Sonuçta elde edilen VSIX hem DSL'ler yükler. F5 kullanarak test edebilir veya dağıtma _YourVsixProject_**\bin\Debug\\\*.vsix**.

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Modelbus'ı Kullanarak Modelleri Tümleştirme](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Nasıl yapılır: Sürükle ve Bırak İşleyicisi Ekleme](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Kopyalama Davranışını Özelleştirme](../modeling/customizing-copy-behavior.md)