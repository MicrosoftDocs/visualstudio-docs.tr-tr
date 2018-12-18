---
title: Dosya Özellikleri, JavaScript
ms.date: 06/21/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: db9809c48b9226e05b7617c860af524b1ac6daf6
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31947930"
---
# <a name="file-properties-javascript"></a>Dosya Özellikleri, JavaScript
Proje sistem dosyalarını gerçekleştirmesi gereken eylemleri belirtmek için dosya özelliklerini kullanabilirsiniz. Örneğin, bir dosya için paket kaynak dosyası olarak eklenmesi gerekip gerekmediğini belirtmek için dosya özelliklerini ayarlayabilirsiniz.

 Çözüm Gezgini'nde herhangi bir dosya seçin ve sonra Özellikler penceresinde özelliklerini inceleyin. JavaScript dosyaları dört özellikleri vardır: **çıktı dizinine Kopyala**, **paket eylemi**, **dosya adı**, ve **dosya yolu**.

## <a name="file-properties"></a>Dosya özellikleri
 Bu bölümde, JavaScript dosyalar için genel özellikleri açıklanmaktadır.

### <a name="copy-to-output-directory-property"></a>Çıktı dizini özelliğine kopyalayın
 Bu özellik, çıkış dizinine altında seçilen kaynak dosya kopyalanacak koşulları belirtir. Seçin **kopyalamayın** dosya hiç çıkış dizinine kopyalanacağını ise. Seçin **her zaman Kopyala** dosyanın çıkış dizinine kopyalanacağını her zaman ise. Seçin **yeniyse Kopyala** dosya yalnızca çıktı dizini içinde aynı ada sahip varolan bir dosyanın daha yeni olduğunda kopyalanacak ise.

### <a name="package-action"></a>Paket eylemi
 **Paket eylem** özelliği, bir yapı çalıştırıldığında Visual Studio bir dosyayla ne yaptığını gösterir. **Paket eylemi** değerlerden biri olabilir:

-   **Hiçbiri** -dosyanın paket bildirimi dahil edilmez. Örnek bir benioku dosyası gibi belgeleri içeren bir metin dosyasıdır.

-   **İçerik** -dosya paketi bildiriminde bulunur. Örneğin, bu ayar bir .htm, .js, .css, görüntü, ses veya video dosyası için varsayılan değerdir.

-   **Bildirim** -dosyanın paket bildirimi dahil edilmez. Bunun yerine, dosya için giriş paket bildirimi oluşturulurken kullanılır. Package.appxmanifest dosyasını için varsayılan değer budur.

-   **Kaynak** -dosyanın paket bildirimi dahil edilmez. Bunun yerine, dosyanın içeriğini paket kaynak dizini (PRI) paket bildirimine gider dizinlenir. Genellikle, kaynak dosyaları için de kullanılır.

İçin varsayılan değer **paket eylem** çözüme eklemek dosya uzantısını bağlıdır.

### <a name="file-name-property"></a>Dosya adı özelliği
 Dosya adı bir salt okunur değeri olarak görüntüler. Dosyayı yeniden adlandırmak için Çözüm Gezgini'nde sağ tıklatın ve seçin **yeniden adlandırma**.

### <a name="full-path-property"></a>Tam yol özelliği
 Tam yolunu dosyaya salt okunur değeri olarak görüntüler. Dosyasının yolunu değiştirmek için sürükle ve bırak Çözüm Gezgini'nde görüntüleyebilirsiniz.

## <a name="reference-file-properties"></a>Başvuru dosyası özellikleri
 Bu bölümde, JavaScript kullanılarak oluşturulmuş bir UWP uygulamasını başvurulan dosyaları ortak özellikleri açıklanmaktadır. Çözüm Gezgini'nde .winmd dosya, bir SDK başvurusu, proje proje başvurusu veya bir derleme başvurusu gibi bir başvuru seçtiğinizde, diğer özellikleri Özellikler penceresinde dosya türüne göre görüntüleyebilir.

### <a name="culture"></a>Kültür
 Başvuru ile ilişkili dili görüntüler.

### <a name="file-type"></a>Dosya türü
 Başvuru dosya türünü görüntüler.

### <a name="file-version"></a>Dosya Sürümü
 Başvuru dosyasının sürümünü görüntüler.

### <a name="identity"></a>Kimlik
 Proje dosyasında depolanan projesinde kullanılan başvuru kimliğini görüntüler.

### <a name="package"></a>Paket
 Başvuru ile ilişkili paket bildirimi adını görüntüler.

### <a name="resolved-path"></a>Çözümlenen yol
 Projede kullanılan başvuru yolunu görüntüler.

### <a name="sdk-path"></a>SDK yolu
 Başvurulan SDK dosyasının yolunu görüntüler.

### <a name="uri"></a>URI
 Dosyanın kaynak dosyası olarak eklenecek projenin HTML veya JavaScript dosyaları dahil gerekir URI görüntüler.

### <a name="version"></a>Sürüm
 Başvuru sürümünü görüntüler.

## <a name="see-also"></a>Ayrıca Bkz.

- [Proje ve Çözüm Özelliklerini Yönetme](../../ide/managing-project-and-solution-properties.md)