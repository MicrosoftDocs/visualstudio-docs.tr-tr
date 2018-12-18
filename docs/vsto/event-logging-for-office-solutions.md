---
title: Office çözümleri için olay günlüğüne kaydetme
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], event viewer
- ClickOnce deployment [Office development in Visual Studio], event viewer
- deploying applications [Office development in Visual Studio], event viewer
- Office development in Visual Studio, event viewer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 267d3e06e9f0d4733a7985f65aa81f368c3f5413
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925122"
---
# <a name="event-logging-for-office-solutions"></a>Office çözümleri için olay günlüğüne kaydetme
  Tarafından yakalanan özel durum iletilerini görmek için Windows Olay Görüntüleyicisi'ni kullanabilirsiniz [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] yüklediğinizde veya Office çözümleri kaldırın. Olay günlüğü ileti, yükleme ve dağıtım sorunlarını gidermek için kullanabilirsiniz.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="read-the-event-log"></a>Olay günlüğünü okuma  
 Açık **Olay Görüntüleyicisi'ni** ve görmek istediğiniz olayları için filtre.  
  
### <a name="to-read-the-event-log-in-windows-server-2003-and-windows-xp"></a>Windows Server 2003 ve Windows XP olay günlüğünde okumak için  
  
1.  Denetim Masası'nda açın **Yönetimsel Araçlar**.  
  
2.  Başlangıç **Olay Görüntüleyicisi'ni**.  
  
3.  Olay günlükleri listesinde seçin **uygulama**.  
  
4.  Üzerinde **görünümü** menüsünde tıklatın **filtre**.  
  
5.  İçinde **olay kaynağı** listesinden **VSTO 4.0**.  
  
6.  Yükleme olayları için de **öğesini belirten Olay No.** kutusuna **4096**.  
  
7.  Tıklayın **Tamam** filtrelenmiş görünümü görmek için.  
  
### <a name="to-read-the-event-log-in-windows-7-windows-vista-and-windows-server-2008"></a>Windows 7, Windows Vista ve Windows Server 2008 olay günlüğünde okumak için  
  
1. Denetim Masası'nda açın **Yönetimsel Araçlar**.  
  
2. Başlangıç **Olay Görüntüleyicisi'ni**.  
  
3. Genişletin **Windows Günlükleri**.  
  
4. Olay günlükleri listesinde seçin **uygulama**.  
  
5. Üzerinde **eylem** menüsünü tıklatın **geçerli günlüğü Filtrele**.  
  
6. İçinde **olay kaynağı** listesinden **VSTO 4.0**.  
  
7. Yükleme olayları için de **öğesini belirten Olay No.** kutusuna **4096**.  
  
8. Tıklayın **Tamam** filtrelenmiş görünümü görmek için.  
  
   Olay Görüntüleyicisi'ni, aşağıdaki bilgileri içerir:  
  
- Çözüm için dağıtım bildiriminin konumunu.  
  
- Hata veya özel durum nedenini açıklayan bir ileti.  
  
  Bu özel durum iletileri, güvenilmeyen bir sertifika, güvenilmeyen dosya konumu veya geçersiz dağıtım bildirimi gibi bir yükleme sorunu nedenini belirlemenize yardımcı olabilir.  
  
  Office çözümünü kaldırıldıktan sonra özel durum iletilerini olay günlüğüne kalır.  
  
  Office çözümünü çalışırken özel durum iletilerini günlüğe kaydet veya göstermek için bkz [hata ayıklama Office projeleri](../vsto/debugging-office-projects.md) ve [hata ayıklama Office projeleri](../vsto/debugging-office-projects.md).  
  
### <a name="localization"></a>Yerelleştirme  
 Özel durum iletisi dili, Office çalışma zamanı dil için Visual Studio Araçları tarafından belirlenir. Örneğin, son kullanıcı bilgisayarına yüklü Japonca dil paketi varsa, özel durum iletisi Japonca olay günlüğüne yazılır.  
  
## <a name="disable-the-event-logger"></a>Olay günlüğü devre dışı bırak  
 Yüklediğinizde veya Office çözümlerini kaldırma olay günlüğü varsayılan olarak etkinleştirilir. Olay günlüğü "1" (bir tane) VSTO_EVENTLOGDISABLED ortam değişkenini ayarlayarak devre dışı bırakabilirsiniz.  
  
### <a name="to-disable-the-event-log"></a>Olay günlüğünü devre dışı bırakmak için  
  
1.  Denetim Masası'nda açın **sistem**.  
  
2.  Üzerinde **Gelişmiş** sekmesinde **ortam değişkenlerini**.  
  
3.  İçinde **sistem değişkenlerini** bölmesinde tıklayın **yeni**.  
  
4.  İçinde **yeni sistem değişkeni** iletişim kutusuna **VSTO_EVENTLOGDISABLED** içinde **değişken adı** kutusu.  
  
5.  İçinde **değişken değeri** kutusuna **1**.  
  
6.  **Tamam**'ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)   
 [Office çözümü dağıtımında sorunlarını giderme](../vsto/troubleshooting-office-solution-deployment.md)  
  
  