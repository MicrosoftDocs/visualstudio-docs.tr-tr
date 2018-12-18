---
title: Team Explorer başvurusu
ms.date: 12/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
ms.author: kaelli
author: KathrynEE
ms.manager: douge
ms.openlocfilehash: 85c7e06482a751b896534c81d227dade74ffbcb5
ms.sourcegitcommit: 5c049194fa256b876ad303f491af11edd505756c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53027559"
---
# <a name="team-explorer-reference"></a>Team Explorer başvurusu

Bu makalede, çeşitli işlevler hakkında Azure DevOps makalelerin bağlantıları sağlanmaktadır **Takım Gezgini**.

Kullanım **Takım Gezgini** kod çabalarınızı diğer takım üyeleri projeyi geliştirmek ve siz, ekibiniz veya projeleriniz için atanan işi yönetmek için koordine etmek için araç penceresi. **Takım Gezgini** Git ve GitHub depoları, Team Foundation sürüm denetimi (TFVC) depolar ve barındırılan projeler için Visual Studio bağlayan [Azure DevOps Hizmetleri](/azure/devops/user-guide/what-is-azure-devops-services) veya bir şirket içi [Azure DevOps sunucu](/tfs/index) (eski adıyla TFS da bilinir). Kaynak kodu, iş öğeleri ve yapıları yönetebilirsiniz.

## <a name="home-page"></a>Giriş sayfası

Çalıştırdıktan sonra [projeye bağlanmanız](../connect-team-project.md) içinde **Takım Gezgini**, aşağıdaki bağlantıları kullanılabilir **proje** bölümü:

- [Depoyu Kopyala](/azure/devops/repos/git/clone)
- [Web portalı](/azure/devops/project/navigation/index)
- [Görev Panosu](/azure/devops/boards/sprints/task-board)

**Giriş** sayfa olup bağlandınız bağlı olarak farklı işlevlere sahip bir [Git](/azure/devops/repos/git/gitquickstart?view=vsts&tabs=visual-studio) veya [Team Foundation sürüm denetimi (TFVC)](/azure/devops/repos/tfvc/overview) depo.

> [!TIP]
> İki sürüm denetim sistemleri bir karşılaştırması için bkz: [(Azure DevOps) projeniz için doğru sürüm denetimini seçin](/azure/devops/repos/tfvc/comparison-git-tfvc).

| **Giriş** Git sayfası | **Giriş** TFVC sayfası |
| - | - |
| ![Visual Studio 2019 Git ile Takım Gezgini giriş sayfası](media/team-explorer-reference/team-explorer-git.png) | ![Visual Studio 2017'de TFVC Takım Gezgini giriş sayfası](media/team-explorer-reference/team-explorer-tfvc.png) |

## <a name="changes-page-git"></a>Değişiklikler sayfası (Git)

Bkz: [çalışmayı işlemelerle kaydetme](/azure/devops/repos/git/commits).

## <a name="branches-page-git"></a>Dallar sayfası (Git)

Bkz: [dallarda iş oluşturma](/azure/devops/repos/git/branches).

## <a name="pull-requests-page-git"></a>Çekme istekleri sayfasına (Git)

Bkz: [çekme isteklerine sahip kodu İnceleme](/azure/devops/repos/git/pullrequest).

## <a name="sync-page-git"></a>Eşitleme sayfasına (Git)

Bkz: [getirme ve çekme ile kodu güncelleştirme](/azure/devops/repos/git/pulling).

## <a name="tags-page-git"></a>Etiketler sayfasını (Git)

Bkz: [Git etiketleri ile çalışma](/azure/devops/repos/git/git-tags).

## <a name="my-work-page-tfvc"></a>Çalışma sayfam (TFVC)

Bkz: [askıya alma/sürdürme iş](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets) ve [kod incelemesi](/azure/devops/repos/tfvc/day-life-alm-developer-suspend-work-fix-bug-conduct-code-review).

## <a name="pending-changes-page-tfvc"></a>Bekleyen değişiklikler sayfası (TFVC)

Bkz: [bekleyen değişiklikleri yönetme](/azure/devops/repos/tfvc/develop-code-manage-pending-changes), [raf kümelerini Bul](/azure/devops/repos/tfvc/suspend-your-work-manage-your-shelvesets), ve [çakışmaları](/azure/devops/repos/tfvc/resolve-team-foundation-version-control-conflicts).

## <a name="source-control-explorer-page-tfvc"></a>Kaynak Denetim Gezgini sayfa (TFVC)

Bkz: [Ekle/görünüm dosya ve klasörleri](/azure/devops/repos/tfvc/add-files-server).

## <a name="work-items-page"></a>İş Öğelerim sayfası

**İş öğeleri** sayfa görmenizi sağlar [iş öğesi](/azure/devops/boards/work-items/about-work-items) sorgular. Bkz.

- [İş öğesi ekleme](/azure/devops/boards/backlogs/add-work-items)
- [Listelemek ve sorguları yönetmek için sorgu Düzenleyicisi'ni kullanın](/azure/devops/boards/queries/using-queries)
- [Sorgu klasörlerini düzenleyin ve sorgu izinlerini ayarlayın](/azure/devops/boards/queries/set-query-permissions)
- [Excel'de sorgu Aç](/azure/devops/boards/backlogs/office/bulk-add-modify-work-items-excel)
- [Projede sorgu açın](/azure/devops/boards/backlogs/office/create-your-backlog-tasks-using-project)
- [Outlook'u kullanarak e-posta sorgu sonuçları listesi](/azure/devops/boards/queries/share-plans)
- [Excel'de sorgudan raporlar oluşturma](/azure/devops/report/excel/create-status-and-trend-excel-reports) (yalnızca TFS)

> [!NOTE]
> Yeni bir [iş öğelerini deneyimi](/azure/devops/boards/work-items/set-work-item-experience-vs) Visual Studio 2019 Önizleme 1. Visual Studio 2019 Preview 1'de iş öğelerini görüntüleme hakkında daha fazla bilgi için bkz: [görünümü ve iş öğelerini eklemek](/azure/devops/boards/work-items/view-add-work-items).

## <a name="builds-page"></a>Yapılar sayfasında

**Yapılar** sayfa sağlar, bkz: derleme tanımları proje için.

Bkz.

- [Derleme işlem hattı oluşturma](/azure/devops/pipelines/tasks/index)
- [Derlemeleri görüntüle ve Yönet](/azure/devops/pipelines/overview)
- [Yapı sırasını yönetin](/azure/devops/pipelines/agents/pools-queues)
- [Visual Studio için sürekli teslim (CD) araçlarını yükleme](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#install-continuous-delivery-cd-tools-for-visual-studio-2017)
- [Yapılandırma ve uygulamanız için sürekli teslim (CD) yürütme](/azure/devops/pipelines/apps/cd/azure/aspnet-core-to-acr#configure-and-execute-continuous-delivery-cd-for-your-app)

## <a name="settings-page"></a>Ayarları sayfası

**Ayarları** sayfa bir proje veya proje koleksiyonu için yönetimsel özellikleri yapılandırmanıza olanak sağlar. Aşağıdaki makalelere bakın:

| Proje | Proje koleksiyonu | Diğer |
| - | - | - |
| [Güvenliği, grup üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Güvenlik, kaynak denetimi (TFVC)](/azure/devops/organizations/security/set-git-tfvc-repository-permissions)<br/>[İş öğesi alanları](/azure/devops/organizations/settings/set-area-paths)<br/>[İş öğesi yinelemeleri](/azure/devops/organizations/settings/set-iteration-paths-sprints)<br/>[Portal ayarları](/azure/devops/report/sharepoint-dashboards/configure-or-add-a-project-portal)<br/>[Proje Uyarıları](/azure/devops/notifications/howto-manage-team-notifications) | [Güvenliği, grup üyeliği](/azure/devops/organizations/security/set-project-collection-level-permissions)<br/>[Kaynak denetimi (TFVC)](/azure/devops/repos/tfvc/decide-between-using-local-server-workspace)<br/>[İşlem Şablonu Yöneticisi](/azure/devops/boards/work-items/guidance/manage-process-templates) | [Git genel ayarlar](/azure/devops/repos/git/git-config)<br/>[Git deposu ayarları](/azure/devops/repos/git/git-config) |

## <a name="see-also"></a>Ayrıca bkz.

- [Takım Gezgini'nde projelerine bağlanma](../../ide/connect-team-project.md)