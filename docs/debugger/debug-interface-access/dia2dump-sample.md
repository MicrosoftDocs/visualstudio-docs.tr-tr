---
title: Dia2dump örneği | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- sample applications [DIA SDK]
- Dia2dump sample [DIA SDK]
ms.assetid: 492c0893-7043-452f-a020-890a47230d20
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2e44abdce737df335133d5e54b6b022c97f639a
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252287"
---
# <a name="dia2dump-sample"></a>Dia2dump Örneği

Dia2dump örneği bir PDB dosyası bilgi sorgulamak için Microsoft hata ayıklama arabirimi erişim Yazılım Geliştirme Seti (DIA SDK) kullanmayı gösterir.

Dia2dump örneği, Visual Studio ile yüklenir ve çözüm ve kaynak dosyaları içerir. Derlenmiş yürütülebilir komut satırından çalıştırır. Bölümlere yalnızca ilginizi çeken veya bir tüm program veritabanı (.pdb) dosyasının içeriğini görüntüleyebilirsiniz.

## <a name="install-the-sample"></a>Örneği yüklemek

Örnek seçeneğini belirlediğinizde yüklü **C++ ile masaüstü geliştirme** Visual Studio Yükleyicisi'nde iş yükü. Visual Studio'yu yükleyin ve belirli iş yükleri ve tek tek bileşenler hakkında daha fazla bilgi için bkz. [Visual Studio'yu yükleyin](../../install/install-visual-studio.md).

Yüklendiğinde, Visual Studio yükleme dizininde \DIA SDK\Samples\DIA2Dump adlı bir alt dizinde örnektir.

## <a name="build-the-sample"></a>Örneği oluşturmak

Varsayılan olarak, yükleme dizini korumalı bir dizindir. Derleme ve bu konuma örnek çözümde düzenleme için bir yükseltilmiş Geliştirici komut istemi veya Visual Studio örneğini kullanmalısınız anlamına gelir. Yapı işlemini basitleştirmek için önce dosyaları örnek dizinden Belgeler klasörünüzde bir klasör gibi başka bir dizine kopyalayın ve ardından örneği oluşturmak öneririz.

### <a name="to-build-the-dia2dump-sample-in-visual-studio"></a>Dia2Dump örneği Visual Studio'da oluşturmak için

1. DIA2Dump.sln dosyasını Visual Studio'da açın. Başka bir dizine çözüm kopyalamayı, Visual Studio'nun yükseltilmiş izinlerle yeniden başlatmanız istenebilir.

1. İçinde **Çözüm Gezgini**, Dia2Dump projeyi (çözümü değil) seçin.

1. Projenin açın **özellik sayfaları** iletişim kutusu. Ayrıntılar için bkz [Working with Project Properties](/cpp/ide/working-with-project-properties).

1. Açık **yapılandırma özellikleri** > **C/C++** > **genel** özellik sayfası.

1. İçinde **ek içerik dizinleri** özelliği aşağı açılır denetimden seçin ve ardından **Düzenle**.

1. İçinde **ek içerik dizinleri** düzenleme alanında iletişim girin `$(VSInstallDir)DIA SDK\include` dizin. Derleyici dia2.h dosya bulabilirsiniz güvence altına almak için bu dizine ekleyin. Seçin **Tamam** yaptığınız değişiklikleri kaydedin.

1. Seçin **Tamam** proje özelliklerine yaptığınız değişiklikleri kaydedin.

1. Üzerinde **derleme** menüsünde seçin **çözümü yeniden derle**. Varsayılan olarak, Visual Studio hata ayıklama çözüm dizininin alt dizininde yer alan örnek bir hata ayıklama sürümünü oluşturur.

1. Visual Studio’yu kapatın.

### <a name="to-build-the-dia2dump-sample-at-the-command-line"></a>Komut satırında Dia2Dump örneği oluşturmak için

1. Bir geliştirici komut istemi penceresinde, örnek dosyalar kopyaladığınız dizine geçin. Örneği başka bir dizine kopyalayın yaramadı yükseltilmiş (yönetici olarak çalıştır) kullanmanız gerekir Geliştirici komut istemi penceresi.

1. Komutu girdikten `nmake makefile` dia2dump.exe varsayılan hata ayıklama yapılandırmasını oluşturmak için.

## <a name="run-the-dia2dump-sample"></a>Dia2Dump örneği çalıştırma

Dia2Dump.exe kullanır üzerinde msdıa*sürüm*.dll COM sunucusunun hizmetlerini sunması için. Visual Studio 2015 ve Visual Studio 2017'de, msdia140.dll sürümüdür. Varsa msdıa*sürüm*değil .dll COM sunucusu başlatılır, dia2dump.exe çalışmadan önce kaydetmeniz gerekir. DIA SDK'sı dizinine sahip x86 içeren bin alt dll Dosyasının sürümü. Bir sürüm için x64 mimarisi makineler bin\amd64 içinde ve bir sürüm ARM için bin\arm içinde. Dll kaydetmek için yükseltilmiş bir geliştirici komut istemi penceresi açın ve makine Mimarinizi sürümü içeren dizine geçin. Komutu girdikten `regsvr32 msdia140.dll` COM sunucuyu kaydetmek için.

### <a name="to-run-the-sample"></a>Örnek çalıştırmak için

1. Bir komut istemi açın ve oluşturulan dia2dump.exe içeren dizine geçin.

1. Komutu girdikten `dia2dump filename` burada *filename* incelemek için bir PDB dosyasının adıdır. PDB dosyası başka bir dizinde ise dosyasının tam yolu kullanmanız *filename*. Bu komut, PDB dosyasında tüm veriler listelenir.

1. Dia2Dump yalnızca seçili bilgileri görüntülemek için diğer seçenekleri vardır. Kullanım `dia2dump -?` tüm kullanılabilir seçenekleri listelemede komutu.

## <a name="see-also"></a>Ayrıca bkz.

- [Taşıma, geçirme ve Visual Studio projelerini yükseltme](../../porting/port-migrate-and-upgrade-visual-studio-projects.md)  
