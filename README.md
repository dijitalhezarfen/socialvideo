# socialvideo

Dijital Hezarfen kısa video paketleri. Bu depoya push edilen her klasör sunucudaki panele yüklenmek üzere **bitmiş bir video paketidir**.

## Düzen

```
videos/
  <İÇERİK-KODU>/            örn. DH-GRW-23
    video.mp4               1080×1920, H.264 + AAC, 30 fps
    cover.jpg               1080×1920 kapak (okunur alan 4:5 orta kırpım içinde)
    subtitles.tr.srt        Türkçe altyazı
    publish.json            başlık, açıklama, etiket, caption, durum (aşağıda)
```

`catalog.json` kökte tüm paketlerin özetini tutar (sıra, kod, başlık, süre, `autoPublish`).

## publish.json

```json
{
  "schema": 1,
  "id": "DH-GRW-23",
  "order": 1,
  "title": "…",
  "durationSeconds": 64.5,
  "video": "video.mp4",
  "cover": "cover.jpg",
  "subtitles": "subtitles.tr.srt",
  "autoPublish": false,
  "publishAt": null,
  "platforms": {
    "youtube": {"title": "…", "description": "…", "tags": ["…"], "privacyStatus": "public", "madeForKids": false, "containsSyntheticMedia": true},
    "instagram": {"caption": "…", "shareToFeed": true, "isAiGenerated": true},
    "facebook": {"description": "…"}
  },
  "production": {"voice": "ElevenLabs eleven_v4 / Kaan Yeni (ses klonu)", "syntheticVoice": true, "videoSha256": "…", "notionPage": "…"}
}
```

- `autoPublish: false` olan paket panelde **taslak** bekler; tarih ve yayın panelden verilir.
- `publishAt` doluysa Europe/Istanbul offset'li ISO zamanıdır.
- Ses ElevenLabs ile üretilmiştir, bu yüzden yapay medya beyanları `true`'dur.
- Sır yok: bu depoda token, anahtar veya hesap bilgisi tutulmaz.
