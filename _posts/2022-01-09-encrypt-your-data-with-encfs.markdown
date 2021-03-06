---
layout: post
title: "رمزگذاری روی پوشه‌ها با encfs در لینوکس"
date: 2022-01-09 08:08:33 +0330
excerpt_separator: <!--more-->
categories:
 - linux
tags:
- linux
- encfs
- encryption
- pendrive
- memory
- hdd
- hard
- external
- unmount
- password
- GUI
- data
- لینوکس
- رمزگذاری
- فلش
- درایو
- هارد
- دیسک
- اکسترنال
- پسورد
- اطلاعات
- رابط
- کاربری
- گرافیکی
---
حتما شما هم روی هارد اکسترنال یا مموری کارت و فلش درایو‌هایتان اطلاعات حساسی دارید که نمی‌خواهید بدست دیگران بیفتد ولی از آنجا که همیشه احتمال گم شدن یا دزدیده شدن شان وجود دارد، بهتر است داده‌های مهمی مثل عکس‌‌ها و فیلم‌های خانوادگی را رمزگذاری کنید تا خیالتان از این بابت اندکی راحت شود.  
<!--more-->
برای رمزگذاری روی فایلها و پوشه‌ها در لینوکس میتوان از `encfs` استفاده کرد.
به این صورت که ابتدا آن را نصب می‌کنیم:
```console
$ sudo pacman -S encfs fuse
```
و با دستورات پایین پوشه `~/.encrypted` را ساخته و قفلش میکنیم در حالی که پوشه `~/decrypted` برای باز کردن قفل و دخل و تصرف در داده‌هاست.  
ابتدا این دو پوشه را می‌سازیم:
```console
$ mkdir ~/.encrypted
$ mkdir ~/decrypted
```
با اجرای دستور زیر `encfs` از ما می‌خواهد حالت رمزگذاری را تعیین کنیم که توصیه میشود `paranoia` را با زدن `p` انتخاب کنید:
```console
$ encfs ~/.encrypted ~/decrypted
```
برای پیاده کردن (unmount)، از این استفاده میکنیم:
```console
$ fusermount -u ~/decrypted
```
برای سوارکردن مجدد هم از دو دستور بالاتر استفاده می‌کنیم و رمزی که داده بودیم را وارد می‌کنیم.  
و با این یکی پسورد را تغییر می‌دهیم:
```console
$ encfsctl passwd ~/.encrypted
```
اگر می‌خواهید از gui استفاده کنید در آرچ لینوکس این بسته را نیز نصب کنید:
```console
$ yay -S  gnome-encfs-manager-bin
```
و به همین ترتیب میتوانید روی داده‌هایتان در هارداکسترنال و فلش درایوها، رمزگذاری کنید.

*[gui]: Graphical user interface