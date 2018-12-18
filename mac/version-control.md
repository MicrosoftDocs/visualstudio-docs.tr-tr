---
title: Sürüm Denetimi
description: Git, Subversion Mac için Visual Studio kullanarak
author: conceptdev
ms.author: crdun
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 0505177e01afd701fe5506df7dd0fc2a2e1f859c
ms.sourcegitcommit: 0a8ac5f2a685270d9ca79bb39d26fd90099bfa29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51294727"
---
# <a name="version-control"></a>Sürüm denetimi

Sürüm denetimi, birçok farklı sürümlere göre dosya yönetimi sistemidir ve - yazılım geliştirme - genellikle katkıda için çok sayıda geliştirici tarafından. Asıl amacı, herhangi bir sürüm denetim sistemidir (_VC'ler_) tüm kullanıcıların kod temeli üzerinde aynı anda çalışmasını sağlayan bir çözümü bulmaktır.

Çekirdek herhangi bir sürüm denetim sistemidir bir _depo_, hangi görür merkezi veri depolamak için tüm farklı dosyalar - bir dosya sunucusuna benzer. Ancak, bir dosya sunucusu, depo proje ve yapılan tüm değişiklikleri tüm geçmişini içerir.

Depo merkezi bir veri deposudur, yerel depolama üzerinde çalışmak için veri sağlamak her bir kullanıcı için mantıksal olur. Bu adlı bir _çalışma kopyası_. Çalışma kopyanızın gibi diğer yerel dizin makinenizde görünür Mac için Visual Studio'da okuma ve yazma dosyalardan birini etmenize imkan sağlar. Ancak, Mac için Visual Studio sürüm denetimi sistemi tümleştirmesi olduğundan, Subversion ve Git IDE'den çıkmadan kullanabilirsiniz.

Subversion tüm dosyaları ve kullanıcıların herhangi bir dosyayı herhangi bir sürümünü denetleyebilirsiniz düzeltmelerini içeren tek bir sunucu olduğu anlamına gelir bir merkezi sürüm denetim sistemidir. Dosyalar uzak Subversion depodan kullanıma, kullanıcı o noktasında depo anlık görüntüsünü alır.

Git takımlar aynı belgelerde aynı anda çalışmasına izin veren bir dağıtılmış sürüm denetim sistemidir. Git ile olabilir tüm dosyaları içeren tek bir sunucu, ancak bu kaynaktan bir depo kullanıma her deponun tamamı makinenizde yerel olarak kopyalanmış olan.

## <a name="basic-concepts"></a>Temel Kavramlar

Mac için Visual Studio hem Git hem de Subversion sürüm denetim sistemleri için destek sağlar. Aşağıdaki makaleleri gözden geçirme, yapılıyor ve değişiklikleri gönderme gibi basit işlevler yanı sıra Mac için Visual Studio ile Git, Subversion deposu ayarlama keşfedin.

* [Git Deposu Ayarlama](set-up-git-repository.md)
* [Git ile çalışma](working-with-git.md)
* [Subversion Deposu Ayarlama](set-up-subversion-repository.md)
* [Subversion ile çalışma](working-with-subversion.md)

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'da sürüm denetimi (Windows üzerinde)](/visualstudio/version-control/)