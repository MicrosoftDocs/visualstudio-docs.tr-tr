---
title: "Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015'e geçirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 09b8950a05c4e4181209190af17eb0d6ccdb35ba
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639714"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015'e geçirme
Uzantınızı yükseltme açıklanmıştır.  
  
> [!IMPORTANT]
>  Visual Studio'nun önceki bir sürümü için uzantı çözümünüzü sürümünü korumak istiyorsanız, yükseltmeden önce bir kopyasını emin olun. Yükseltilmiş sürümü önceki durumuna geri döndürmek zor olabilir.  
  
### <a name="to-upgrade-an-extensibility-solution"></a>Genişletilebilirlik çözümünü yükseltmek için  
  
1.  Kopyalama kullanarak istediğiniz yükseltme yeni sürümünde açın. Yükseltme geri alınamaz olduğunu önerilecektir.  
  
2.  Yükseltme tamamlandıktan sonra en yeni sürümüne dış program yolunu değiştirmek *devenv.exe*. ' Nde proje düğümüne sağ **Çözüm Gezgini**, ardından **özellikleri**. İçinde **hata ayıklama** sekmesinde, metin kutusu tarafından Bul **harici program Başlat** ve yolunu değiştirmek *devenv.exe* Visual Studio 2015 yoluna hangi görünmelidir aşağıdakine benzer:  
  
     *%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe*  
  
3.  Bir başvuru ekleyin *Microsoft.VisualStudio.Shell.14.0.dll*. ('nde proje düğümüne sağ **Çözüm Gezgini** seçip **Ekle** > **başvuru**. Select **uzantıları** sekmesini ve ardından **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Çözümü oluşturun. Yerleşik dosyaları dağıtılır:  
  
     *%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< yazar adı\>\\< proje adı\>\\< proje sürüm\>\\*.  
  
### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Bir genişletilebilirlik projesi için NuGet VS SDK başvurusu derlemeleri'nin güncelleştirmek için  
  
1.  Projenize gereken VS SDK başvurusu derlemeleri'nin belirleyin.  İçinde **Çözüm Gezgini**, projenin genişletin **başvuruları** düğüm ve proje başvuruları listesini gözden geçirin.  VS SDK başvuru bütünleştirilmiş kodları önekine sahip olacak **Microsoft.VisualStudio** adında (örneğin: Microsoft.VisualStudio.Shell.14.0).  
  
2.  Bunları, sütuna sağ tıklayıp seçerek VS SDK başvurusu derlemeleri'nin projeden Kaldır **Kaldır**.  
  
3.  VS SDK başvurusu derlemeleri'nin NuGet sürümlerini ekleyin.  Yine **Çözüm Gezgini başvuruları** düğümü, açık **NuGet paketlerini Yönet** iletişim.  Bu iletişim kutusu hakkında daha fazla bilgi edinmek istiyorsanız bkz [Paket Yöneticisi UI](/NuGet/Tools/Package-Manager-UI). VS SDK başvurusu derlemeleri'nin yayımlanan [nuget.org](http://www.nuget.org) tarafından [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Kullanarak **nuget.org** olarak, **paket kaynağı**, istenen başvuru bütünleştirilmiş kodu ile eşleşen NuGet paket adı arayın (örneğin: Microsoft.VisualStudio.Shell.14.0) ve içinde yükleme, Proje.  NuGet, ilk derleme bağımlılıklarını karşılamak için birden fazla başvuru bütünleştirilmiş kodları ekleyebilirsiniz.  
  
     İsterseniz, tüm VS SDK başvurusu derlemeleri'nin tek seferde VS SDK'sını yükleyerek ekleyebileceğiniz [Meta paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Ayrıca NuGet sürümü VS SDK derleme araçlarını kullanarak geçiş yapabilirsiniz. Bu NuGet paketi [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) ve bir kez eklenen projenize gerekli araçlar içerir ve hedef dosyaların genişletilebilirlik projenize bir bilgisayarda yüklü VS SDK oluşturmanıza olanak sağlar.  
  
> [!NOTE]
>  Bu, var olan genişletilebilirlik projeleri NuGet başvuru bütünleştirilmiş kodları ve araçları kullanmak için güncelleştirme gerekiyor.  Bunlar, başvuru bütünleştirilmiş kodları ve araçları VS SDK'sı ile yüklü kullanarak oluşturmaya devam edebilirsiniz.