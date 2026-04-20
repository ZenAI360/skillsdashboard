# Skills Dashboard

> 🇹🇷 Türkçe açıklama aşağıda · 🇬🇧 English description below

---

## 🇹🇷 Türkçe

### Nedir?

**Skills Dashboard**, yüklü tüm Claude skill'lerini tek bir sayfada görselleştiren, arayabileceğiniz ve düzenleyebileceğiniz saf HTML/CSS/React uygulamasıdır. Hiçbir kurulum gerektirmez — tek bir `.html` dosyasını tarayıcıda açmanız yeterlidir.

🥳İlham: Peter Guirguis'in Skills Arsenal projesinden esinlenildi.

### Özellikler

| Özellik | Açıklama |
|---|---|
| **Akıllı Arama** | İsim, açıklama, tetikleyici ifade ve kategori üzerinden ağırlıklı puanlama ile arama |
| **3 Arama Modu** | Akıllı Arama · İsme Göre · Tetikleyiciye Göre |
| **Kategori Sekmeleri** | 8 kategori; seçilen kategori skoru filtreleme yapar |
| **Gruplu Görünüm** | "Tümü" sekmesinde skill'ler kategoriye göre alfabetik gruplanır |
| **Favoriler** | Yıldız butonuyla skill'leri sabitleme; localStorage'a kaydedilir |
| **Son Görüntülenenler** | Tıklanan son 6 skill otomatik izlenir; daraltılabilir bölüm |
| **Çakışma Tespiti** | Tetikleyici veya isim benzerliğine göre örtüşen skill gruplarını otomatik bulur |
| **Spotlight** | Rastgele bir skill öne çıkarılır; yenile butonu başka birini seçer |
| **Kaynak Dağılımı** | Kaynakları ve sayılarını gösteren genişletilebilir panel |
| **8 Renk Teması** | Elektrik Mavi · Gök Mavisi · Zümrüt · Gün Batımı · Gül · Altın · Mor · Buz Mavisi |
| **Karanlık / Aydınlık Mod** | Sistem tercihini okur; localStorage'a kaydedilir |
| **3 Yerleşim** | Izgara · Liste · Dergi (magazin) |
| **Yoğunluk** | Ferah · Sıkı |
| **Skill Yükleme** | SKILL.md dosyalarını klasörden seçerek yükle |
| **Otomatik Reload** | `.claude/skills` klasöründen tek tıkla tüm skill'leri yeniden yükle (File System Access API + IndexedDB) |
| **Yazdırma** | Baskıya özel stil: gereksiz bölümler gizlenir, tetikleyiciler görünür |
| **Klavye Kısayolları** | `/` → arama kutusuna odaklan · `Escape` → odağı kaldır / modalı kapat |
| **TR / EN** | Tüm arayüz Türkçe ve İngilizce desteğiyle gelir |
| **localStorage Kalıcılığı** | Favori, son görüntülenen, tema, renk, yerleşim tercihleri tarayıcıya kaydedilir |

---

### Tepe Menüsü — Buton Rehberi

```
┌─────────────────────────────────────────────────────────────┐
│  ⚡ Skills Dashboard          [15 skill] [🖨] [🎨] [⚙] [📁] [↺] [☽/☀]  │
└─────────────────────────────────────────────────────────────┘
```

#### ⚡ Marka & Skill Sayacı
Sol taraftaki **yıldırım simgesi** ve başlığın yanındaki **"15 skill"** rozeti, o anda yüklü toplam skill sayısını canlı gösterir. Kendi skill'lerinizi yüklediğinizde otomatik güncellenir.

---

#### 🖨 Yazdır
Sayfayı yazıcıya gönderir. Baskıda şunlar gizlenir:
- Üst çubuk, hero bölümü, istatistikler, spotlight, favoriler, son görüntülenenler, çakışma uyarısı, sekmeler, alt bilgi, arka plan efektleri
- Tetikleyici ifadeler **görünür** olarak açılır
- Kağıt dostu beyaz arka plan ve siyah metin uygulanır

---

#### 🎨 Renk Teması Seç
8 vurgu rengi arasından seçim yapmanızı sağlayan bir modal açar. Seçilen renk:
- Tüm CSS değişkenlerini (`--accent`, `--accent-light`, vb.) günceller
- Arka plan orb renklerini değiştirir
- Aktif sekme, kart üst çizgisi, arama odağı, rozetler dahil tüm vurgu noktalarına yansır
- `localStorage` anahtarı `sk_color`'a kaydedilir

| Tema | Renk |
|---|---|
| Elektrik Mavi | `#3D7AF5` |
| Gök Mavisi | `#0ea5e9` |
| Zümrüt | `#10b981` |
| Gün Batımı | `#f97316` |
| Gül | `#f43f5e` |
| Altın | `#f59e0b` |
| Mor | `#8b5cf6` |
| Buz Mavisi | `#06b6d4` |

---

#### ⚙ İnce Ayarlar (Tweaks)
Ekranın sağ alt köşesinde bir panel açar. İçindeki ayarlar:

| Ayar | Seçenekler |
|---|---|
| **Yerleşim** | Izgara (varsayılan) · Liste · Dergi |
| **Yoğunluk** | Ferah (varsayılan) · Sıkı |
| **Arka Plan** | Orb animasyonu Açık · Kapalı |
| **Dil** | TR · EN |

Tüm ayarlar `localStorage` (`sk_tweaks`) anahtarına kaydedilir.

---

#### 📁 Klasörden Yükle
Dosya seçici açar; bir veya birden fazla `SKILL.md` dosyası seçmenize olanak tanır.

- Seçilen her `SKILL.md` ayrıştırılır: `name:` ve `description:` alanları okunur
- Açıklamadan tetikleyici ifadeler ve "best for" cümlesi çıkarılır
- Kategori, açıklama içeriğinden otomatik tahmin edilir
- Yüklenen skill'ler demo verilerin **yerine geçer** ve `localStorage`'a (`sk_custom`) kaydedilir
- Tarayıcı desteklemiyorsa ya da SKILL.md bulunamazsa uyarı toast'ı gösterilir

> **Not:** Yüklenen skill'leri kaldırmak için sayfayı yenileyip `sk_custom` localStorage anahtarını temizleyin.

---

#### ↺ Otomatik Reload (.claude/skills)
`.claude/skills` klasörünüzdeki tüm SKILL.md dosyalarını **tek tıkla** tarayıp arayüze yükler.

**İlk kullanımda:**
1. Tarayıcı bir klasör seçici açar
2. `.claude\skills` klasörünü seçin
3. Klasör izni IndexedDB'ye kaydedilir

**Sonraki kullanımlarda:**
- Klasör seçici çıkmaz; izin hâlâ geçerliyse otomatik okur
- İzin sürerse tarayıcı yalnızca izin ister, klasör seçimi istemez
- Alt klasörler **recursive** taranır; her `SKILL.md` bulunur

Yükleme sırasında ikon döner 🔄. Tamamlanınca kaç skill yüklendiğini bildiren bir bildirim gösterilir.

> **Tarayıcı uyumluluğu:** File System Access API — Chrome 86+, Edge 86+. Firefox'ta bu buton çalışmaz; 📁 Klasörden Yükle butonu kullanılabilir.

---

#### ☽ / ☀ Karanlık / Aydınlık Mod
Pill şeklindeki toggle, karanlık ve aydınlık mod arasında geçiş yapar.
- Sayfa ilk açıldığında sistem tercihinizi (`prefers-color-scheme`) okur
- Seçim `sk_mode` anahtarıyla localStorage'a kaydedilir
- Geçiş `html[data-theme]` özniteliği üzerinden CSS değişkenleriyle yapılır

---

### Skill Kartı

Her kart şunları içerir:

- **Başlık** — Skill adı
- **Açıklama** — 2 satıra kırpılmış (genişletince tümü görünür)
- **Kaynak rozeti** — Renkli kaynak etiket (Cowork Essentials, Marketing, vb.)
- **Kategori rozeti** — Hangi kategoriye ait olduğunu gösterir
- **En iyi:** — Skill'in en ideal kullanım senaryosu (italik, vurgu rengiyle)
- **⭐ Favori butonu** — Tıklayarak sabitleme
- **Tetikleyici İfadeler** — Karta tıklayınca açılır; Claude'u tetiklemek için kullanılan monospace chip'ler

**Kart etkileşimleri:**
- Hover → kart hafifçe yükselir, üstte gradient şerit belirir
- Tıklama → tetikleyici bölümü genişler, açıklama kliplenme kaldırılır

---

### Kurulum & Kullanım

```bash
# Repo'yu klonlayın
git clone https://github.com/KULLANICI_ADINIZ/skills-dashboard.git

# Klasöre girin
cd skills-dashboard

# Skills Dashboard.html dosyasını tarayıcıda açın
# (Chrome veya Edge önerilir — File System Access API desteği için)
```

Hiçbir bağımlılık yok. Sunucu gerekmez. Dosyayı çift tıklayarak açabilirsiniz.

---

### Kendi Skill'lerinizi Yüklemek

`SKILL.md` dosyaları YAML frontmatter formatında olmalıdır:

```markdown
---
name: skill-adi
description: Skill'in ne yaptığını açıklayan bir veya birkaç cümle.
  Use when users mention "tetikleyici ifade 1", "tetikleyici ifade 2".
---
```

Dashboard, `name:` ve `description:` alanlarını ayrıştırır; `"..."` içindeki ifadeleri tetikleyici olarak çıkarır.

---

### Lisans

MIT

---
---

## 🇬🇧 English

### What is it?

**Skills Dashboard** is a zero-dependency, single-file HTML/CSS/React application that lets you visualize, search, and curate all your installed Claude skills in one place. No build step, no server — just open `Skills Dashboard.html` in a browser.

🥳 Inspired by Peter Guirguis's “Skills Arsenal” project.

### Features

| Feature | Description |
|---|---|
| **Smart Search** | Weighted relevance scoring across name, description, triggers, and category |
| **3 Search Modes** | Smart Search · By Name · By Trigger |
| **Category Tabs** | 8 categories; selecting one filters the grid instantly |
| **Grouped View** | In "All" tab, skills are grouped under collapsible, alphabetically sorted category headers |
| **Favorites** | Star any skill to pin it; persisted to localStorage |
| **Recently Viewed** | Last 6 opened skills are tracked automatically; collapsible section |
| **Duplicate Detection** | Automatically finds overlapping skill groups by trigger or name similarity |
| **Spotlight** | A random skill is highlighted; a refresh button picks another |
| **Source Breakdown** | Expandable panel showing each source and its skill count |
| **8 Color Themes** | Electric Blue · Sky · Emerald · Sunset · Rose · Amber · Violet · Cyan Ice |
| **Dark / Light Mode** | Reads system preference on load; saved to localStorage |
| **3 Layouts** | Grid · List · Magazine |
| **Density** | Comfy · Compact |
| **Skill Import** | Load SKILL.md files by selecting a folder |
| **Auto Reload** | One-click reload of all skills from your `.claude/skills` folder (File System Access API + IndexedDB) |
| **Print Styles** | Print-optimised stylesheet: noise hidden, triggers visible, white background |
| **Keyboard Shortcuts** | `/` → focus search · `Escape` → blur / close modal |
| **TR / EN** | Full bilingual interface |
| **localStorage Persistence** | Favorites, recents, theme, color, and layout preferences survive page reloads |

---

### Header Buttons — Reference Guide

```
┌─────────────────────────────────────────────────────────────┐
│  ⚡ Skills Dashboard      [15 skills] [🖨] [🎨] [⚙] [📁] [↺] [☽/☀]  │
└─────────────────────────────────────────────────────────────┘
```

#### ⚡ Brand & Skill Counter
The **lightning bolt logo** on the left and the **"15 skills" badge** next to it show the total number of currently loaded skills in real time. Updates automatically when you import your own skills.

---

#### 🖨 Print
Sends the page to the printer. Print stylesheet hides:
- Header, hero, stats, spotlight, favorites, recents, duplicate banner, tabs, footer, ambient effects
- Trigger phrases are **expanded** and visible
- Clean white background with black text is enforced

---

#### 🎨 Choose Accent Color
Opens a modal with 8 color swatches. Selecting one:
- Updates all CSS custom properties (`--accent`, `--accent-light`, etc.)
- Changes ambient orb colors
- Reflects on active tabs, card top-bar, search focus ring, badges, and all accent points
- Saved to `localStorage` key `sk_color`

| Theme | Color |
|---|---|
| Electric Blue | `#3D7AF5` |
| Sky | `#0ea5e9` |
| Emerald | `#10b981` |
| Sunset | `#f97316` |
| Rose | `#f43f5e` |
| Amber | `#f59e0b` |
| Violet | `#8b5cf6` |
| Cyan Ice | `#06b6d4` |

---

#### ⚙ Tweaks Panel
Opens a panel in the bottom-right corner with four settings:

| Setting | Options |
|---|---|
| **Layout** | Grid (default) · List · Magazine |
| **Density** | Comfy (default) · Compact |
| **Background** | Orbs On · Orbs Off |
| **Language** | TR · EN |

All settings are saved to `localStorage` (`sk_tweaks`).

---

#### 📁 Load from Folder
Opens a file picker allowing you to select one or more `SKILL.md` files.

- Each `SKILL.md` is parsed: `name:` and `description:` fields are extracted
- Trigger phrases and a "best for" sentence are inferred from the description
- Category is auto-detected from description keywords
- Loaded skills **replace** the demo data and are saved to `localStorage` (`sk_custom`)
- A warning toast is shown if no SKILL.md files are found

> **Note:** To revert to demo data, reload the page and clear the `sk_custom` localStorage key.

---

#### ↺ Auto Reload (.claude/skills)
Scans your `.claude/skills` folder **recursively** and loads every `SKILL.md` into the dashboard with a single click.

**First use:**
1. The browser opens a directory picker
2. Navigate to and select your `.claude\skills` folder
3. The directory handle is saved in IndexedDB

**Subsequent clicks:**
- No picker appears — reads automatically if permission is still valid
- If permission expires, the browser asks only for re-permission, not folder selection again
- All sub-folders are traversed recursively

The icon spins 🔄 during loading. A toast notification reports how many skills were loaded.

> **Browser support:** File System Access API — Chrome 86+, Edge 86+. Not available in Firefox; use the 📁 folder button instead.

---

#### ☽ / ☀ Dark / Light Mode Toggle
The pill-shaped toggle switches between dark and light mode.
- On first load, reads your system preference (`prefers-color-scheme`)
- Saved to `localStorage` key `sk_mode`
- Mode switches via `html[data-theme]` attribute driving CSS custom properties

---

### Skill Card Anatomy

Each card contains:

- **Title** — Skill name
- **Description** — 2-line clamped (expands on click)
- **Source badge** — Color-coded source label (Cowork Essentials, Marketing, etc.)
- **Category badge** — Which category the skill belongs to
- **Best for:** — Ideal use-case summary (italic, accent color)
- **⭐ Favorite button** — Pin/unpin the skill
- **Trigger Phrases** — Expands on card click; monospace chips showing the phrases that invoke the skill in Claude

**Card interactions:**
- Hover → card lifts slightly, gradient top-bar fades in
- Click → trigger section expands, description unclamps

---

### Getting Started

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/skills-dashboard.git

# Enter the folder
cd skills-dashboard

# Open Skills Dashboard.html in your browser
# (Chrome or Edge recommended — for File System Access API support)
```

No dependencies. No server. You can double-click the file to open it.

---

### Loading Your Own Skills

`SKILL.md` files should follow YAML frontmatter format:

```markdown
---
name: skill-name
description: One or more sentences describing what the skill does.
  Use when users mention "trigger phrase one", "trigger phrase two".
---
```

The dashboard parses the `name:` and `description:` fields and extracts quoted strings as trigger phrases.

---

### localStorage Keys Reference

| Key | Type | Description |
|---|---|---|
| `sk_color` | string | Active accent theme ID |
| `sk_mode` | string | `dark` or `light` |
| `sk_lang` | string | `tr` or `en` |
| `sk_favs` | JSON array | IDs of starred skills |
| `sk_recent` | JSON array | IDs of last 6 viewed skills |
| `sk_collapsed` | JSON object | Collapsed state per category |
| `sk_recent_collapsed` | `"0"` / `"1"` | Recently viewed section collapsed state |
| `sk_tweaks` | JSON object | Layout, density, orbs settings |
| `sk_custom` | JSON array | User-loaded skill objects |

---

### License

MIT
