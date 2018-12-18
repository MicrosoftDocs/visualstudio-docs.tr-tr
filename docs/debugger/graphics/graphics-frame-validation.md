---
title: Grafik Çerçeve doğrulama | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cdfdee83a9c78069b3f086ef84b280ba9328e4f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49850886"
---
# <a name="graphics-frame-validation"></a>Grafik Çerçeve doğrulama
<!-- VERSIONLESS --> Visual Studio 2017 ve daha büyük Destek **çerçeve doğrulama** aracı.  Çerçeve doğrulama penceresi, hataları ve olay listesi ile ilişkili uyarıları görüntüler.  Bu pencereyi görüntülemek için seçin **Görüntüle > Çerçeve doğrulama** menüsü.

![Çerçeve Doğrulama](media/gfx_diag_frame_validation.png)

Tıklayın **doğrulama çalışması** analiz başlatmak için sol üst köşedeki düğmesini.  Bu çerçeve karmaşıklığına bağlı olarak tamamlanması birkaç dakika sürebilir.  İki farklı kaynaktan gelen bir birleşimini aşağıdadır görüntülenen verileri: iletileri bu D3D kendisini ne zaman yayar [SDK katmanları](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) etkinleştirilmiş ve İzleme Aracı'nın kendi iç durumu toplanan verileri. İşlem tamamlandıktan sonra birkaç veri sütunlarının görürsünüz:


| **Sütun** | **Açıklama** |
|------------| - |
| Olay Kimliği | İçindeki bir girdiye eşleştiren kimliği [olay listesi](graphics-event-list.md) penceresi. |
| Önem Derecesi | Bozulma, hata, uyarı, bilgi veya ileti. |
| Kategori | Tanımlanmış, çeşitli uygulama başlatma, temizleme, derleme, durum oluşturma, durumu ayarı, durum alma, yürütme, kaynak düzenlemesi, gölgelendirici, gereksiz ve kullanılmayan. |
| İleti | Olayla ilişkili ileti. |
| Olay | Hata veya uyarı ile ilişkili olay. |

## <a name="see-also"></a>Ayrıca Bkz.  
[Grafik tanılama (DirectX grafik hata ayıklama)](visual-studio-graphics-diagnostics.md)   
<!-- /VERSIONLESS -->