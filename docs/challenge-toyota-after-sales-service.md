# TOYOTA After-Sales Service Challenge Brief

## Status

Active challenge direction.

Previous challenge-direction files and data have been removed from the repo so future brainstorming should use this document as the source of truth.

## Team

Jarvis計畫

## Challenge Topic

運用 AI 再造 TOYOTA 下一代顧客售後服務體驗

## Challenge Description

在 TOYOTA，交車僅是顧客關係的開端，「售後服務」才是維繫品牌忠誠度的核心。每一次回廠保養與維修，都是與顧客建立信任的關鍵時刻。

隨著顧客數量穩健成長，服務廠的單日入廠車流日益提升。車主回廠時，服務專員會進行初步接待說明，車主隨後進入客休室等待。然而，在尖峰時段，服務專員面對高接待量與時間壓力，加上自身豐富的車輛知識與車主之間可能存在資訊不對稱，較難在有限時間內提供讓每位車主都滿意且易懂的維修解說。因此，提案應提升接待溝通的品質與效率。

同時，客休室提供的服務與設備行之有年。提案也應思考如何將客休等待時間轉化為更具價值、更符合現代車主需求的嶄新體驗。

參賽者可利用公開輿情蒐集、車主訪談、服務流程觀察，並輔以 GenAI 進行情境模擬與分析，深入挖掘接待說明與客休等待過程中的具體痛點，提出精準的解決方案。目標是在高效服務的同時，創造讓車主有感、甚至超乎預期的接待體驗，深化品牌與顧客之間的信任關係。

## Expected Goal

站在未來車主的角度，運用 GenAI 與資料分析能力，設計一套兼顧以下目標的 AI 顧客服務解決方案：

- 提升服務效率。
- 提升溝通品質。
- 提供個人化體驗。
- 創造客休等待期間的新價值。
- 深化顧客對 TOYOTA 售後服務的信任與回廠意願。

## Required Proposal Outcomes

### 1. 發掘痛點與需求分析

需運用公開輿情、訪談資料、服務流程資料或情境模擬，分析顧客在接待說明與客休等待過程中的潛在需求或期望。

需要界定：
- 現行服務痛點。
- 顧客資訊不對稱來源。
- 尖峰時段下服務專員的溝通壓力。
- 客休等待時間的未被滿足需求。
- 後續解決方案的依據。

### 2. 提出創新 AI 解決方案

基於痛點，設計一套以 AI 為核心的具體解決方案。

需清楚說明：
- 產品運作流程。
- 功能描述。
- 使用者體驗規劃。
- 實際應用場景。
- AI 如何協助服務專員與車主。

可能形式：
- 新功能。
- 互動工具。
- 數位服務。
- 客休室互動體驗。
- 接待說明輔助系統。

### 3. 洞察服務體驗中的關鍵創新因子

需說明解決方案如何發掘並創造「品牌高峰體驗（Peak Experience）」。

可以思考：
- 哪些服務環節最能提升顧客信賴感？
- 哪些互動可以提高滿意度？
- 如何設計更具記憶點與差異化的體驗？
- 是否能延伸成新的服務機會或潛在商機？
- 如何讓客休等待時間不只是等待，而是有價值的互動？

### 4. 預期效益與落地評估

需評估方案導入台灣 TOYOTA 服務廠的：
- 預期效益。
- 落地可行性。
- 潛在導入門檻。
- 可衡量成效指標。

可衡量指標例：
- 縮短接待說明時間。
- 降低重複詢問率。
- 提升顧客滿意度。
- 提高 APP / LINE 互動率。
- 提升回廠意願。
- 提升維修說明理解度。
- 降低服務專員尖峰負荷。

## Official / Suggested Resources

### Vehicle Service Information

車輛原廠服務資訊可參考：
- TOYOTA 車主指南網站。
- 網路搜尋相關開箱影片或文章，以了解實體服務廠情境。

### Provided Reference Documents

Expected files or sources:
- TOYOTA 官方 LINE 預約操作手冊。
- TOYOTA 回廠服務流程手冊。
- TOYOTA 售後服務競賽資料 archive.

Local reference archive:

```text
data/raw/toyota_after_sales_competition_data.7z
```

### Data Usage Assumptions

提案設計中，可合理假設 AI 系統能串接並讀取 TOYOTA 內部資料：
- 車主歷史保養紀錄。
- 車輛行車數據。
- APP 互動行為數據。

用途：
- 規劃個人化 AI 體驗。
- 支援接待前摘要。
- 支援維修說明個人化。
- 支援客休等待期間的互動推薦。

### Public Online Community Data

參賽團隊需自行運用網路社群公開資料集，蒐集 TOYOTA 相關討論文本作為分析基礎。

可分析方向：
- 車主對保養流程的抱怨與期待。
- 對維修費用說明的理解落差。
- 對等待時間的情緒與需求。
- 對 LINE / APP 預約體驗的意見。
- 對服務專員說明品質的評價。
- 對客休室體驗與設備的期待。

## Initial Brainstorming Directions

### Direction A: AI 接待說明副駕

幫服務專員在接待前快速生成車主摘要、保養重點、可能疑問與白話說明，降低尖峰接待壓力。

Potential features:
- 車主歷史保養摘要。
- 本次回廠可能項目。
- 費用與工項白話解釋。
- 車主可能關心問題預測。
- 服務專員話術建議。

### Direction B: 客休室 AI 維修透明化體驗

把等待時間轉化為「理解我的車」的互動體驗。

Potential features:
- 維修進度卡。
- 本次保養項目白話說明。
- 車況健康分數。
- 下次保養提醒。
- 個人化用車建議。
- LINE / APP 即時互動問答。

### Direction C: Peak Experience 設計

在服務流程中創造一個讓車主覺得「TOYOTA 很懂我」的高峰時刻。

Possible peak moments:
- 服務前：AI 主動整理「今天為什麼需要做這些項目」。
- 等待中：用互動式畫面解釋技師正在檢查什麼。
- 交車前：生成一份個人化車況摘要與未來保養建議。
- 離廠後：透過 LINE / APP 發送一份清楚、可回看的服務摘要。

### Direction D: AI 服務溝通品質監控

以 AI 協助管理服務說明品質，確保不同服務廠與不同服務專員的溝通一致性。

Potential features:
- 接待說明 checklist。
- 常見問題與標準回答。
- 說明完整度檢查。
- 顧客情緒與疑慮標籤。
- 後續追蹤建議。

## Initial Non-Goals

For the first proposal iteration, avoid overcommitting to:
- 完整取代服務專員。
- 直接判斷保固責任或最終維修價格。
- 未經同意串接或使用個資。
- 未確認官方 API 可行性就承諾 live integration。
- 把公開網路輿情當成官方結論。

## Immediate Next Steps

1. Inspect the TOYOTA reference archive and summarize available materials.
2. Decide the primary product concept for the proposal.
3. Rebuild proposal slides around TOYOTA after-sales service only.
4. Define pain-point analysis method using public data, interviews, service-flow observation, or GenAI simulation.
5. Draft measurable outcomes and ROI assumptions after research.
