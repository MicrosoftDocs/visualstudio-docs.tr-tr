---
title: "Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015'e geçirme | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio SDK, upgrading
ms.assetid: 22491cdc-8f04-4e1c-8eb4-ff33798ec792
caps.latest.revision: 26
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 564e279d259cae879ca2925eed3309c30d7513db
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51785163"
---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2015"></a>Nasıl yapılır: genişletilebilirlik projelerini Visual Studio 2015'e geçirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uzantınızı yükseltme açıklanmıştır.  
  
> [!IMPORTANT]
>  Visual Studio'nun önceki bir sürümü için uzantı çözümünüzü sürümünü korumak istiyorsanız, yükseltmeden önce bir kopyasını emin olun. Yükseltilmiş sürümü önceki durumuna geri döndürmek zor olabilir.  
  
#### <a name="to-upgrade-an-extensibility-solution"></a>Genişletilebilirlik çözümünü yükseltmek için  
  
1.  Kopyalama kullanarak istediğiniz yükseltme yeni sürümünde açın. Yükseltme geri alınamaz olduğunu önerilecektir.  
  
2.  Yükseltme tamamlandıktan sonra dış program yolu Devenv.exe yeni sürüm olarak değiştirin. ' Nde proje düğümüne sağ **Çözüm Gezgini**, ardından **özellikleri**. İçinde **hata ayıklama** sekmesinde, metin kutusu tarafından Bul **harici program Başlat** ve şunun gibi görünmelidir Visual Studio 2015 yoluna devenv.exe yolunu değiştirin:  
  
     **%ProgramFiles%\Microsoft visual Studio 14.0\Common7\IDE\devenv.exe**  
  
3.  Microsoft.VisualStudio.Shell.14.0.dll bir başvuru ekleyin. ('nde proje düğümüne sağ **Çözüm Gezgini** seçip **ekleyin / Reference**. Select **uzantıları** sekmesini ve ardından **Microsoft.VisualStudio.Shell.14.0**.)  
  
4.  Çözümü oluşturun. Yerleşik dosyaları dağıtılır:  
  
     **%LocalAppData%\Microsoft\VisualStudio.14.0Exp\Extensions\\< yazar adı\>\\< proje adı\>\\< proje sürüm\>\\**.  
  
#### <a name="to-update-an-extensibility-project-to-nuget-vs-sdk-reference-assemblies"></a>Bir genişletilebilirlik projesi için NuGet VS SDK başvurusu derlemeleri'nin güncelleştirmek için  
  
1.  Projenize gereken VS SDK başvurusu derlemeleri'nin belirleyin.  İçinde **Çözüm Gezgini**, projenin genişletin **başvuruları** düğüm ve proje başvuruları listesini gözden geçirin.  VS SDK başvuru bütünleştirilmiş kodları önekine sahip olacak **Microsoft.VisualStudio** adında (örneğin: Microsoft.VisualStudio.Shell.14.0).  
  
2.  VS SDK başvurusu derlemeleri'nin seçerek projeden kaldırmak için sağ tıklayın ve **Kaldır**.  
  
3.  VS SDK başvurusu derlemeleri'nin NuGet sürümlerini ekleyin.  Yine **Çözüm Gezgini başvuruları** düğümü, açık **NuGet paketlerini Yönet...** iletişim kutusu.  Bu iletişim kutusu hakkında daha fazla bilgi edinmek istiyorsanız bkz [yönetme NuGet paketlerini kullanarak iletişim](http://docs.nuget.org/Consume/Package-Manager-Dialog). VS SDK başvurusu derlemeleri'nin yayımlanan [nuget.org](http://www.nuget.org) tarafından [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility).  
  
4.  Kullanarak **nuget.org** olarak, **paket kaynağı**, istenen başvuru bütünleştirilmiş kodu ile eşleşen NuGet paket adı arayın (örneğin: Microsoft.VisualStudio.Shell.14.0) ve içinde yükleme, Proje.  NuGet, ilk derleme bağımlılıklarını karşılamak için birden fazla başvuru bütünleştirilmiş kodları ekleyebilirsiniz.  
  
     İsterseniz, tüm VS SDK başvurusu derlemeleri'nin tek seferde VS SDK'sını yükleyerek ekleyebileceğiniz [Meta paket](http://www.nuget.org/packages/VSSDK_Reference_Assemblies).  
  
5.  Ayrıca NuGet sürümü VS SDK derleme araçlarını kullanarak geçiş yapabilirsiniz. Bu NuGet paketi [Microsoft.VSSDK.BuildTools](http://www.nuget.org/packages/Microsoft.VSSDK.BuildTools) ve bir kez eklenen projenize gerekli araçlar içerir ve hedef dosyaların genişletilebilirlik projenize bir bilgisayarda yüklü VS SDK oluşturmanıza olanak sağlar.  
  
> [!NOTE]
>  Bu, var olan genişletilebilirlik projeleri NuGet başvuru bütünleştirilmiş kodları ve araçları kullanmak için güncelleştirme gerekiyor.  Bunlar, başvuru bütünleştirilmiş kodları ve araçları VS SDK'sı ile yüklü kullanarak oluşturmaya devam edebilirsiniz.

