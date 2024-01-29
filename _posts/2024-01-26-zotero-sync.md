---
title: "Zetero使用非官方云存储同步文献库"
date: 2024-01-20
permalink: /posts/2024-01-26-zotero-sync/
collection: posts
tags:
  - Zotero
  - Sync
  - OneDrive
---

今天将文献管理软件从Mendeley迁移到了Zotero。主要原因有几个：

- 原来的Mendeley Desktop已经不再更新，新版的Mendeley Reference Manager客户端就是一个完全基于云端的浏览器套壳，打开文档有加载时间，使用不顺滑；
- 导入文献的浏览器插件Mendeley Web Importer很不好用，很慢并且经常导入失败；
- Zotero是开源软件，更新频率高，社区活跃。

Zotero很好，但是Zotero自己服务器的同步功能对于免费用户只有300MB的存储空间，如果有大量的文献，这个空间很快就会被占满。需要同步文献库的原因是，如果有两台电脑，我需要在两台电脑上都能够使用Zotero并且保持一致。如果只使用一台电脑，其实不同步也是可以的。

本文介绍如何使用非官方的云存储来同步Zotero的文献库。

## 下载安装Zotero

Zotero的官网是[zotero.org](https://www.zotero.org/)，在这里可以下载到Zotero的安装包，这里不再赘述。

## 迁移Mendeley文献库至Zotero

Zotero提供了一键迁移Mendeley文献库的功能，只需要点击Zotero的菜单栏中的`File`->`Import`->`Mendeley Reference Manager`即可，登录Mendeley账号就可迁移。

![import mendeley](/figures/2024-01-26-zotero-sync-1.png)

## Zotero同步设置

首先需要注册并登录Zotero账号，去官网注册账号，然后点击工具栏Edit->Preferences->Sync，输入账号密码即可。

如果Mendeley导入的文献库超过了300MB, 这时候点击右上角的同步按钮，会有一个警告，提示由于超出容量，无法完全同步。来到[Zotero Storage](https://www.zotero.org/settings/storage)的页面，可以看到容量使用情况。

![Zotero Storage](/figures/2024-01-26-zotero-sync-2.jpg)

官网提供容量升级方案，但是需要额外付费。同时，Zotero也提供了其他的同步方案，这点还是非常良心的。在这个页面: [https://www.zotero.org/support/sync#alternative_syncing_solutions](https://www.zotero.org/support/sync#alternative_syncing_solutions) 可以看到Zotero提供的其他同步方案。比如最简单的方式是：

> The easiest method is to use linked files, rather than stored copies of files, with only your attachment files in the externally synced folder. The ZotFile plugin can make this simple by automatically moving attachment files to a designated folder as you import them. You should also set up Zotero's Linked Attachment Base Directory feature to point to the same folder so that Zotero can find your files on each computer, even if the path to the cloud storage folder differs.

也就是用ZotFile插件，将附件文件（也就是文献的PDF文件）转移到一个云盘在本地的文件夹，该文件夹便会使用云盘自动进行同步。然后ZotFile会自动设置链接指向这些外部文件，这样便实现了文献库元数据（例如文献的标题，作者，DOI等）和附件的分离，元数据存储在Zotero服务器上，附件存储在云盘上。元数据的大小远远小于附件的大小，使用Zotero服务器是完全够用的。

这里我使用的是OneDrive来同步附件，因为我已经和人合租了Office 365 Family，OneDrive的存储空间是1TB，足够使用了。如果你使用的是其他的云存储，比如iCloud，Google Drive，Dropbox等，也是可以的，方法是一样的。

## 下载安装ZotFile

ZotFile是Zotero的一个插件，官网是[zotfile.com](https://zotfile.com/)，在这里可以下载到ZotFile的安装包。下载后点击Zotero菜单中的`Tools`->`Add-ons`->`Install Add-on From File...`，选择下载的ZotFile安装包即可。如下图所示：

![install ZotFile](/figures/2024-01-26-zotero-sync-3.png)

## 设置ZotFile

安装完ZotFile后，点击Zotero菜单中的`Tools`->`ZotFile Preferences`，打开ZotFile的设置界面。如下图所示：

![ZotFile Preferences](/figures/2024-01-26-zotero-sync-4.png)

在`General Settings`中，设置`Source Folder for Attaching New Files`为你的下载文件夹，如`C:\Users\username\Downloads`，这一步是为了方便以后将下载的文献PDF文件转移到云盘文件夹中。这样，如果你选中一篇文献，右键并选择`attach new file`，ZotFile会自动将该文献的PDF文件从下载文件夹转移到云盘文件夹中，并且自动设置链接指向云盘文件夹中的文件。

然后设置`Location of Files`为你的云盘文件夹，这里我设置为`C:\Users\username\OneDrive\Zotero`，其中`username`是你的Windows用户名。`Zotero`文件夹是我在OneDrive中新建的，用于存储文献附件。

## 转移文献附件

这时候，已经在文献库中的文献附件还没有转移到云盘的Zotero文件夹中，首次转移需要手动进行。在Zotero点击左侧的My Library，按`ctrl+A`全选文献，然后点击右键，选择`Manage Attachments`->`Rename and Move`，等待几分钟，所有的文献附件就会转移到云盘的Zotero文件夹（这里是`C:\Users\username\OneDrive\Zotero`）中了。OneDrive会自动进行同步。

## 设置Zotero的附件文件夹

在Zotero中，点击`Edit`->`Preferences`->`Advanced`->`Files and Folders`，将`Linked Attachment Base Directory`设置为你的云盘文件夹，这里是`C:\Users\username\OneDrive\Zotero`。如下图所示：

![Zotero Preferences](/figures/2024-01-26-zotero-sync-5.png)

这一步设置的目的是因为在不同的电脑上，云盘文件夹的路径可能不同，比如在Windows上可能是`C:\Users\username\OneDrive\Zotero`，在Mac上可能是`/Users/username/OneDrive/Zotero`，这样设置后，Zotero就可以找到这个云盘目录作为Base Directory，然后在Base Directory下找到文献附件。

## Purge Storage in My Library

完成上述步骤后，理论上Zotero的文献附件应该全部转移到了云盘中，但如果点击右上角的同步按钮，还是会有警告。这是因为Zotero的服务器上还有一些文献附件，需要手动删除（这可能是同步的一个bug）。这时需要到[Zotero Storage](https://www.zotero.org/settings/storage)的页面，点击`Purge Storage in My Library`，然后再回到Zotero客户端，点击右上角的同步按钮，这时候就不会有警告了。

## 在其他电脑上同步

以上步骤完成后，Zotero就实现了完全的云同步。在其他电脑上，只需要安装Zotero和ZotFile，登录Zotero账号，同样设置一下ZotFile和`Linked Attachment Base Directory`，然后点击右上角的同步按钮，就可以同步文献库了。
