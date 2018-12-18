---
title: Yük Testi Senaryosu Özellikleri
ms.date: 10/19/2016
ms.topic: reference
helpviewer_keywords:
- load tests, properties
- load tests, scenarios
ms.assetid: 4414a638-1fa2-40ad-b1f4-b99f90b62e62
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-ide-test
ms.openlocfilehash: 65508c3a7594c0943b80fbbb898c62b0fc013557
ms.sourcegitcommit: ae46be4a2b2b63da7e7049e9ed67cd80897c8102
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52894605"
---
# <a name="load-test-scenario-properties"></a>Yük testi senaryosu özellikleri

Yük testi senaryo özellik ayarları Visual Studio Yük testi gereksinimlerini karşılayacak şekilde değiştirin. Bu makalede, çeşitli yük testi senaryosu özellikleri kategoriye göre listelenmektedir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="general"></a>Genel

|Özellik|Tanım|
|-|----------------|
|**Ad**|Senaryonun adı.|

## <a name="mix"></a>Karışımı

|Özellik|Tanım|
|-|----------------|
|**Tarayıcı karışımı**|Yük testi için web tarayıcısı karışımını belirtir. Farklı bir web tarayıcı türleri ve yük dağılımını belirtebilirsiniz.<br /><br />Üç noktayı seçin **(...)**  açmak için düğmeyi **Tarayıcı Karışımını Düzenle** iletişim ve kullanım **Ekle** ve **Kaldır** yük testinde web tarayıcısı türlerini seçmek için.<br /><br />Daha fazla bilgi için [web tarayıcısı türlerini belirtmek](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Ağ karışımı**|Yük testi için ağ karışımını belirtir. Dahil etmek için hangi ağ türlerini ve bunların yük dağıtımı belirtebilirsiniz.<br /><br />Üç noktayı seçin **(...)**  açmak için düğmeyi **Ağ Karışımını Düzenle** iletişim kutusu ve kullanım **Ekle** ve **Kaldır** yük testinde ağ türlerini seçin.<br /><br />Daha fazla bilgi için [sanal ağ türlerini belirtme](../test/specify-virtual-network-types-in-a-load-test-scenario.md).|
|**Test karışımı**|Web performans ve birim karışımı yük testi için test belirtir. Hangi testlerin ekleneceğini ve bunların yük dağıtımı belirtebilirsiniz.<br /><br />Üç noktayı seçin **(...)**  açmak için düğmeyi **Test Karışımını Düzenle** iletişim kutusu ve kullanım **Ekle** ve **Kaldır** yük testinde testleri seçmek için.<br /><br />Daha fazla bilgi için [bir yük testi senaryosu için test karışımını Düzenle](../test/edit-the-test-mix-to-specify-which-web-browsers-types-in-a-load-test-scenario.md).|
|**Test karışımı türü**|Yük testi için test karışımı modelini belirtir.<br /><br />Üç noktayı seçin **(...)**  açmak için düğmeyi **Test Karışımını Düzenle** iletişim kutusu ve altındaki aşağı açılan kullanım **Test karışımı modeli** yük testinde kullanılacak test karışımı modeli seçin.<br /><br />Daha fazla bilgi için [karışımı modellerini düzenleme](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md).|

## <a name="options"></a>Seçenekler

|Özellik|Tanım|
|-|----------------|
|**Kullanılacak Aracılar**|Senaryonuz yükü çalıştırıyorsanız kullanmak istediğiniz aracıları uzaktan test belirtir. Örneğin, performans eğilimlerini analiz ederken tutarlılık sağlamak için belirli bir aracı kümesi belirtmek isteyebilirsiniz. Ayrıca, hangi betiklerin arasında çalıştırdığı ve aracıyı bulunduğu benzeşim yani aracıları coğrafi olarak dağıtılabilir.<br /><br />Aracıları ayrılmalıdır virgüllerle, örneğin "**agent1'e, birim testi Agent2, Aracı3**". Özellik boş bırakılırsa, senaryo kullanılabilir tüm aracılar kullanması gerektiğini belirtir.<br /><br />Daha fazla bilgi için [nasıl yapılır: belirtin test aracıları kullanmayı](../test/how-to-specify-test-agents-to-use-in-load-test-scenarios.md).|
|**Adım Gecikmesine dağıtımı Uygula**|Test karışımı modeli Adımlama kullanıcının tipik dağıtım gecikmelerine isteyip istemediğinizi belirtmek için kullanılan Boole değeri. Bu özellik yalnızca geçerlidir **Test karışımı türü** özelliği **kullanıcı adımı tabanlı**.<br /><br />Daha fazla bilgi için [nasıl yapılır: Adım Gecikmesine dağıtımı Uygula](../test/how-to-apply-distribution-to-pacing-delay-when-using-a-user-pace-test-mix-model.md)|
|**IP geçişi**|IP geçişi kullanılıp kullanılmadığını belirtmek için kullanılan Boole değeri.<br /><br />IP geçişi, bir dizi farklı IP adreslerini kullanarak bir sunucuya istek göndermek bir test aracısı sağlar. Bu, farklı istemci bilgisayarlardan gelen çağrıların benzetimini yapar. Yük dengeli web grubu karşı test ettiğinizde, IP geçişi önemlidir. Çoğu yük dengeleyicileri, istemcinin IP adresini kullanarak bir istemci ve belirli bir web sunucusu arasında benzeşim kurar. Tüm istekler tek bir istemciden geliyor gibi görünüyorsa, yük dengeleyicisi yükü dengelemez. Web grubunda iyi bir yük dengesi edinmek için istekleri bir dizi IP adreslerinden geldiğini önemlidir.<br /><br />IP geçişi, yalnızca test aracısı ile kullanılabilir.|
|**En yüksek Test Yinelemeleri**|Senaryoda çalıştırılacak testlerin sayısını belirtmek için kullanılan sayısal değer. 0 değeri en büyük değer belirtir.<br /><br />Daha fazla bilgi için [senaryolar için test yinelemelerini yapılandırma](../test/configure-test-iterations-in-a-load-test-scenario.md).|
|**Yeni kullanıcıların yüzdesi**|Bu senaryoda yeni kullanıcılar ya da ilk ziyaretçi yüzdesini belirtir sayısal değer.<br /><br />Daha fazla bilgi için [nasıl yapılır: web önbellek verilerini kullanan sanal kullanıcıların yüzdesini belirtme](../test/how-to-specify-the-percentage-of-virtual-users-that-use-web-cache-data.md).|
|**Düşünme profili**|Senaryo kullanıp kullanmayacağını belirtir **Normal dağıtım**, veya Düşünme profili **üzerinde** veya **kapalı**.<br /><br />Daha fazla bilgi için [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme düzenleme kez](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="timing"></a>Zamanlama

|Özellik|Tanım|
|-|----------------|
|**Gecikme başlangıcı zamanı**|Kaç saat, dakika ve saniye cinsinden gecikme yükleme sonrası senaryoyu başlatmadan başladığında test belirten bir zaman değeri. Varsa **Isınma sırasında devre dışı bırak** özelliği **True**, beklenecek zaman miktarı Isınma döneminin tamamlanmasından sonra uygulanır.<br /><br />Daha fazla bilgi için [Senaryo Başlatma Gecikmelerini Yapılandırma](../test/configure-scenario-start-delays.md).|
|**Isınma sırasında devre dışı bırak**|Senaryo çalışıp çalışmaması gerektiğini sırasında değil belirtmek için kullanılan bir Boole değeri **Isınma Süresi** yük testi içinde belirtilen özellik zaman değeri ayarı çalıştırmasını.<br /><br />Yük testi çalıştırma ayarı özellikleri hakkında daha fazla bilgi için bkz. [yük testi çalıştırma ayarları özellikleri](../test/load-test-run-settings-properties.md).<br /><br />Daha fazla bilgi için [Senaryo Başlatma Gecikmelerini Yapılandırma](../test/configure-scenario-start-delays.md).|
|**Test Yinelemeleri Arasındaki Düşünme**|Test yinelemeleri arasındaki saniyeler içinde bekleme süresini belirtmek için kullanılan sayısal değer.<br /><br />Daha fazla bilgi için [Web sitesi insan etkileşimi gecikmelerini benzetmek için düşünme düzenleme kez](../test/edit-think-times-in-load-test-scenarios.md).|

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)