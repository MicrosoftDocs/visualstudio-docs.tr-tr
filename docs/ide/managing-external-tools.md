---
title: Dış araçları yönetme
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.externaltools
helpviewer_keywords:
- external tools [Visual Studio]
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: eeeee2e6e7ae5d043124faaa79bc6bad7c527702
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31945889"
---
# <a name="manage-external-tools"></a>Dış araçları yönetme

Dış Araçları'ndan çağırabilirsiniz kullanarak Visual Studio içinde **Araçları** menüsü. Birkaç varsayılan araçları mevcuttur **Araçları** menü ve özelleştirebilirsiniz menü diğer yürütülebilir kendi ekleyerek.

## <a name="tools-available-on-the-tools-menu"></a>Araçlar menüsünde kullanılabilen Araçlar

**Araçları** menüsü birkaç yerleşik komutları gibi içerir:

* **Uzantılar ve güncelleştirmeler** için [Visual Studio uzantılarını yönetme](finding-and-using-visual-studio-extensions.md)
* **Kod parçacıkları Yöneticisi** için [kod parçacıkları düzenleme](code-snippets.md)
* **PreEmptive tarafından koruması - Dotfuscator** başlatmak için [Dotfuscator Community Edition (CE)](dotfuscator/index.md) , [yüklü](dotfuscator/install.md)
* **Özelleştir** için [menüleri ve araç çubuklarını özelleştirme](how-to-customize-menus-and-toolbars-in-visual-studio.md)
* **Seçenekler** için [çeşitli Visual Studio IDE ve diğer araçları için farklı seçenekleri ayarlama](reference/options-dialog-box-visual-studio.md)

## <a name="add-new-tools-to-the-tools-menu"></a>Araçlar menüsünde yeni araçları ekleme

Dış bir araç çubuğunda görünmesini ekleyebilirsiniz **Araçları** menüsü.

1. Açık **Harici Araçlar** seçerek iletişim kutusu **Araçları** > **Harici Araçlar**.

1. Tıklatın **Ekle**ve bilgileri doldurun. Örneğin, şu girdiyi neden **Windows Explorer** dosya dizininde açmak için şu anda Visual Studio'da Aç yok:

   * Başlık: `Open File Location`

   * komut: `explorer.exe`

   * Bağımsız değişkenler: `/root, "$(ItemDir)"`

   ![Dış araçlar iletişim kutusu](media/external-tools-dialog.png)

Bir dış aracı tanımlarken kullanılabilir değişkenlerin tam listesi verilmiştir:

|Ad|Bağımsız Değişken|Açıklama|
|----------|--------------|-----------------|
|Öğe yolu|$(ItemPath)|Geçerli dosyasının tam dosya adı (sürücü + yolu + dosya adı).|
|Öğe dizini|$(ItemDir)|Geçerli bir dosya (sürücü + yolu) dizini.|
|Öğe dosya adı|$(ItemFilename)|Dosyasının dosya adını geçerli (dosya adı).|
|Öğe uzantısı|$(ItemExt)|Geçerli dosyanın dosya adı uzantısı.|
|Geçerli satır|$(CurLine)|İmleç kod penceresinde geçerli satır konumu.|
|Geçerli sütun|$(CurCol)|İmleç kod penceresinde geçerli sütun konumu.|
|Geçerli metin|$(CurText)|Seçili metni.|
|Hedef yolu|$(TargetPath)|Oluşturulacak öğesinin tam dosya adı (sürücü + yolu + dosya adı).|
|Hedef Dizin|$(TargetDir)|Oluşturulacak öğenin dizini.|
|Hedef Adı|$(TargetName)|Oluşturulacak öğenin dosya adı.|
|Hedef uzantısı|$(TargetExt)|Oluşturulacak öğenin dosya adı uzantısı.|
|İkili dizin|$(BinDir)|Oluşturulmakta olan ikili (sürücü + yolu tanımlanan) son konumu.|
|Proje dizini|$(ProjDir)|Geçerli projenin (sürücü + yolu) dizini.|
|Proje dosyası adı|$(ProjFileName)|Geçerli projenin dosya adı (sürücü + yolu + dosya adı).|
|Çözüm dizini|$(SolutionDir)|Geçerli çözüme (sürücü + yolu) dizini.|
|Çözüm dosyası adı|$(SolutionFileName)|Dosya adı, geçerli çözüme (sürücü + yolu + dosya adı).|

> [!NOTE]
> IDE durum çubuğu görüntüler **geçerli satır** ve **geçerli sütun** ekleme noktasını etkin bulunduğu belirtmek için değişkenleri **Kod düzenleyicisinde**. **Geçerli metin** metin ya da bu konumda seçili kod değişkeni döndürür.

## <a name="see-also"></a>Ayrıca bkz.

- [C/C++ derleme araçları](/cpp/build/reference/c-cpp-build-tools)
