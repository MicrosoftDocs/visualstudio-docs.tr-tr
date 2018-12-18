---
title: Test etmek için tanılama veri bağdaştırıcısı oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Diagnostic Data Adapter [Visual Studio ALM]
- Diagnostic Data Adapter
ms.assetid: b0b53fae-7007-4ad9-a604-21685937622f
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 67eb1a1128a811868db97dfc682c7b4eec7b2c61
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53068075"
---
# <a name="create-a-diagnostic-data-adapter-to-collect-custom-data-or-affect-a-test-machine"></a>Özel veri toplayan veya test makinesini etkileyen tanılama veri bağdaştırıcısı oluşturma

Test çalıştırma ya da testinizi bir parçası olarak test makinesini etkilemek isteyebileceğiniz verileri toplamak için kendi tanılama veri bağdaştırıcısı oluşturmak isteyebilirsiniz. Örneğin, test altındaki uygulamanız tarafından oluşturulan ve bunları test sonuçlarınızı ekleme, günlük dosyaları toplamak isteyebilirsiniz veya bilgisayarınızda sol sınırlı disk alanı olduğunda, testlerinizi çalıştırmak isteyebilirsiniz. Visual Studio Enterprise içinde sağlanan API'leri kullanarak, test çalıştırmanızda belirli noktalarda görevler gerçekleştirmek için kod yazabilirsiniz. Örneğin, bir testi başlamadan önce ve sonra her bir testi çalıştırdığınızda ve test çalıştırması bittiğinde görevleri gerçekleştirebilirsiniz.

Özel tanılama veri bağdaştırıcınızı yapılandırma ayarları dosyasının kullanarak varsayılan giriş sağlayabilirsiniz. Örneğin, dosyanın konumu hakkında bilgi toplamak ve test sonuçlarına istediğiniz sağlayabilir veya ne kadar disk alanı sistemde bırakılması istediğiniz. Bu veriler, oluşturduğunuz her test ayarları için yapılandırılabilir. Görüntülenen ve bir düzenleyici olarak kullanmak için kendi kullanıcı denetiminizi düzenlenen Microsoft Test Yöneticisi'ni veya, sağlanan varsayılan Düzenleyicisi'ni kullanarak oluşturabilirsiniz. Düzenleyici bağdaştırıcısı yapılandırmasında yapılan değişiklikleri ile test ayarlarınızın depolanır.

Testlerinizi Visual Studio'dan çalıştırıyorsanız, bunları ayarlamalısınız etkin olması için test ayarları. Test ayarları hakkında daha fazla bilgi için bkz. [test ayarlarını kullanarak tanılama bilgi toplayan](../test/collect-diagnostic-information-using-test-settings.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="tasks"></a>Görevler

Tanılama veri bağdaştırıcıları oluşturmanıza yardımcı olması için aşağıdaki konulara bakın:

|Görevler|İlişkili Konular|
|-|-----------------------|
|**Tanılama veri bağdaştırıcısı oluşturma:** bir sınıf kitaplığı oluşturarak tanılama veri bağdaştırıcısı oluşturmak ve ardından istediğiniz veya testlerinizi çalıştırmak için kullandığınız bir test sistemini etkilemek bilgilerini toplamak için tanılama veri bağdaştırıcısı API'leri kullanın.|-   [Nasıl yapılır: tanılama veri bağdaştırıcısı oluşturma](../test/how-to-create-a-diagnostic-data-adapter.md)|
|**Özel tanılama veri bağdaştırıcısı kullanan testler için seçme çalıştırılır:** bağdaştırıcı, testlerinizi çalıştırdığınızda kullanılır, böylece hangi tanılama veri bağdaştırıcısı test ayarlarınız için kullanmayı seçebilirsiniz.|-   [(Azure Test planları) test sırasında tanılama verilerini toplayın](/azure/devops/test/collect-diagnostic-data?view=vsts)<br />-   [El ile testlerde (Azure Test planları) tanılama verilerini toplayın](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)|

## <a name="see-also"></a>Ayrıca bkz.

- [Test ayarlarını kullanarak tanılama bilgileri Topla](../test/collect-diagnostic-information-using-test-settings.md)