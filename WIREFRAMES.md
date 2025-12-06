# New Year Art Cards Web App – Mobile-First Wireframes

## 1) もらった年賀絵一覧 (Inbox)

```
[Top Tabs]  もらった | 送った

[Year Section Label: 2025]
┌─────────────────────────────┐
| [Card][Card][Card] → horiz scroll  |
| thumb + soft shadow + rounded      |
└─────────────────────────────┘
[Year Section Label: 2024]
┌─────────────────────────────┐
| [Card][Card][Card] → horiz scroll  |
└─────────────────────────────┘
(Repeat for older years)

Bottom padding for safe area
```

**Component hierarchy**
- Page
  - TopTabBar (primary nav: もらった, 送った)
  - YearSections (stacked vertical)
    - YearHeader (label)
    - CardRow (horizontal scroll / 2–3 per row on mobile)
      - ArtCard
        - Thumbnail (1:1 or 4:5, soft shadow, rounded)
        - Subtle overlay for hover/touch
  - SafeAreaPadding / Spacer

---

## 2) 送った年賀絵一覧 (Outbox)

```
[Top Tabs]  もらった | 送った (active)

[Year Section Label: 2025]
┌─────────────────────────────┐
| [Card][Card][Card] → horiz scroll  |
└─────────────────────────────┘
[Year Section Label: 2024]
┌─────────────────────────────┐
| [Card][Card][Card] → horiz scroll  |
└─────────────────────────────┘

[Floating Action Button] bottom-right: 「＋ 新規作成」

Bottom padding for safe area
```

**Component hierarchy**
- Page
  - TopTabBar (same as Inbox)
  - YearSections (stacked)
    - YearHeader
    - CardRow
      - ArtCard (same pattern)
  - FloatingActionButton (primary action: create new art)
  - SafeAreaPadding / Spacer

---

## 3) 詳細画面（画像 + チャット同一画面）

```
[Top: Back arrow / Title / Year tag]

[Image Carousel Frame]
┌─────────────────────────┐
| ←  [Large Art Image]  → |
| (rounded, drop shadow)  |
└─────────────────────────┘
[Metadata Bar]
- URL (copy icon)
- Sender/Receiver name pill
- Tag chips: #高校 友人  #前職 同僚

[Divider]

[Chat Area – stays on same page]
┌─────────────────────────┐
| AI/System messages (gray bubbles)  |
| User messages (accent bubbles)     |
| Input bar: text field + Send       |
| Hint: "この絵の意味は？"            |
└─────────────────────────┘

Bottom spacing for keyboard-safe area
```

**Component hierarchy**
- Page
  - HeaderBar (Back, Title/Year, overflow)
  - ImageSection
    - ImageFrame (fixed ratio 1:1 or 4:5)
      - NavArrowLeft / NavArrowRight
      - ArtImage
    - MetadataBar
      - URLChip (copy icon)
      - NamePill (sender/receiver)
      - TagChips (list)
  - Divider
  - ChatSection (DM style)
    - MessageList
      - MessageBubble (user / AI variants)
    - InputBar (text field, send button, hint text)
  - SafeAreaPadding

---

## 4) 新規作成画面（画像生成＋条件フォーム）

```
[Top Bar: Back / Title]

[Preview Frame – 1:1 or 4:5]
┌─────────────────────────┐
|  AI-generated preview    |
└─────────────────────────┘
[Button Row]
- 「再生成」 | 「スタイル変更」 (side-by-side on mobile, expand on desktop)

[Form Section – always below preview]
1) Image Style Selection
   [Style Card] [Style Card] [Style Card] (selectable)
2) Keyword Tags (chips)
   #結婚  #多忙  #新生活  #転職  ...
3) My Info (optional toggle per field)
   - Address [include toggle]
   - Workplace [include toggle]
   - Family structure [include toggle]
4) Free Message
   [Multiline text box]

[Primary CTA button: 「生成してシェアURLを作成」]

Bottom spacing for safe area
```

**Component hierarchy**
- Page
  - HeaderBar
  - PreviewSection
    - PreviewFrame (fixed ratio)
    - ActionButtons (Regenerate, Change Style)
  - FormSection (stacked cards)
    - StyleSelector (selectable cards)
    - KeywordChips (multi-select)
    - MyInfoSelectors
      - InfoFieldRow (label, value, toggle to include)
    - FreeMessageInput (multiline)
  - PrimaryCTAButton
  - SafeAreaPadding

---

## 5) マイページ (Profile)

```
[Top Bar: Back / Title]

[Profile Form Card]
- Address (text input)
- Contact info (phone / email)
- Family structure (text)
- Occupation / workplace (text)
- Consent toggle: 「この情報を年賀絵生成に使ってよい」

[Save Button]

Bottom spacing / safe area
```

**Component hierarchy**
- Page
  - HeaderBar
  - ProfileFormCard
    - AddressField
    - ContactField
    - FamilyField
    - OccupationField
    - ConsentToggle
  - SaveButton
  - SafeAreaPadding

---

## Brief Rationale
- Mobile-first single-column layout keeps focus on the artwork and chat; desktop centers content with comfortable max-widths and soft margins.
- Card rows with subtle shadows evoke a calm “bookshelf/collection” metaphor, matching the annual keepsake feel.
- Detail screen keeps chat on the same page to preserve context and immediacy; image occupies upper half with clear arrow navigation.
- Creation flow keeps preview on top so users see regenerated results immediately, with conditions stacked below to prevent hidden settings.
- Warm, minimal components (rounded cards, chips, soft shadows) maintain a friendly, lightweight New Year aesthetic without heavy animations.
