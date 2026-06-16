---
title: "Osmanlıca Rumi Takvimden Miladi Takvime Dönüşümün İncelikleri"
date: 2026-06-01
tags: ["csharp", "osmanlica", "tarih", "kutuphane"]
categories: ["Yazılım"]
series: ["Tirnavali.Converter"]
author: "tirnavali"
---

## Problem

Osmanlı arşiv belgelerinde tarihler genellikle Rumi (Mali) takvimle kaydedilmiştir. Bu tarihleri Miladi takvime dönüştürmek, tarihsel belge işleme sistemlerinde sık karşılaşılan bir ihtiyaçtır.

## Rumi Takvim Nedir?

Rumi takvim, Osmanlı İmparatorluğu'nda 1839'dan itibaren mali işlerde kullanılmaya başlanan, Jülyen takvimi temelli bir takvimdir. Miladi takvimle arasında:

- 13 günlük sabit fark (1900 öncesi: 12 gün)
- Ay isimleri farklılığı bulunur

## Çözüm: Tirnavali.Converter.BasicRumiToGregorian

Açık kaynak bir C# kütüphanesi olarak geliştirdiğim bu dönüştürücü:

```csharp
using Tirnavali.Converter;

// Rumi tarihi Miladi'ye çevir
var rumiDate = new RumiDate(1341, RumiMonth.Mart, 15);
DateTime gregorianDate = RumiToGregorian.Convert(rumiDate);
// Sonuç: 15 Mart 1925
```

## Karşılaşılan Zorluklar

### 1. Artık Yıl Hesaplaması

Rumi ve Miladi takvimler farklı artık yıl kurallarına sahiptir. 1900 yılı artık yıl değilken Rumi'de özel durumlar vardır.

### 2. Yıl Başlangıcı

Rumi yılbaşı 1 Mart'tır. Bu, Ocak ve Şubat aylarında yıl dönüşümünü etkiler.

### 3. Tarihsel Doğrulama

Bazı Rumi tarihler tarihsel olarak geçersiz olabilir (örneğin takvim değişikliklerinin olduğu dönemler).

## Kullanım Alanları

- Arşiv belgesi dijitalleştirme
- Osmanlıca metin işleme
- Tarihsel veri analizi

[NuGet paketi →](https://www.nuget.org/) | [GitHub →](https://github.com/tirnavali/Tirnavali.Converter.BasicRumiToGregorian)
