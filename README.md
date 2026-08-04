
# 💰 Financial & P&L Analysis Dashboard (End-to-End Business Intelligence Project)

> نظام تحليل مالي وقوائم دخل متكامل، مصمم لتمكين الإدارة العليا من مراقبة الأداء المالي، تتبع الإيرادات والمصروفات، وعمل محاكاة مالية لحظية لدعم اتخاذ القرار.

---

## 📌 1. Project Overview & Business Problem
في عالم الـ Business Intelligence، الأرقام وحدها لا تكفي؛ بل القدرة على محاكاة المستقبل وتحليل الأثر المالي لكل قرار هي ما يصنع الفارق. يهدف هذا المشروع إلى بناء نظام مالي احترافي يربط بين الأداء الفعلي وقوائم الأرباح والخسائر (Profit and Loss - P&L)، مع توفير رؤى واضحة حول كفاءة التشغيل، سلوك العملاء، وتركز المبيعات.

---

## 🏗️ 2. Data Modeling & Architecture
القصة بدأت من رحلة البيانات؛ اعتمدنا على Fact Tables واضحة للإيرادات (`Revenue`) والمصروفات (`Expenses`)، وربناها بـ Dimension Tables هندسية تخدم طبيعة الحسابات الهرمية لقوائم الدخل (`P&L`) مثل (`dAccount` و `dAccountHeader`)، بالإضافة إلى جدول المنتجات (`dProduct`) والجدول الزمني (`Calendar Table`). التصميم هنا ليس مجرد Star Schema تقليدية، بل هو موديل مهجن مخصص يتحمل تداخلات الحسابات المالية المعقدة ويضمن أن سرعة الاستعلامات والفلترة تكون في أعلى مستوى.

> `![Data Model](https://github.com/MahmoudAtef-Data/Financial-P-L-Analysis-Dashboard/blob/main/DATA%20MODEL.png)

---

## ⚙️ 3. Core DAX Measures & What-If Logic
وعشان نحول الموديل ده لعقل ذكي بيحسب ويفكر، وظّفنا معادلات DAX متقدمة تخدم الـ Cards والـ Charts اللي قدام عيون الإدارة:

### 🔹 أ. معادلة صافي الدخل والمحاكاة الديناميكية (`INCOME-WTF`)
دمج متغيرات الـ What-If Parameters مع الإيرادات والتكاليف لتوقع الأرباح لحظياً:
```dax
INCOME-WTF = 
VAR SelectedQtyChange = SELECTEDVALUE('WhatIf_Parameter'[Value], 1)
VAR AdjustedRevenue = [Total Revenue] * SelectedQtyChange
VAR AdjustedCosts = [Total Cost] * SelectedQtyChange
RETURN
      AdjustedRevenue - AdjustedCosts - [Total Expenses]

🔹 ب. نسبة إجمالي الهامش (GM %)

لحساب الهامش بدقة مع حماية الموديل ضد أخطاء القسمة على صفر:
مقتطف الرمز

GM % = 
DIVIDE([Gross Profit], [Total Revenue], 0)

🔹 ج. معادلات الـ Time Intelligence

استخدام دوال مثل TOTALYTD لتتبع تراكم أداء الحسابات وبنود الـ P&L عبر الفترات المالية المختلفة.

    📷 [ضع صورة للداشبورد وهي تعرض الكاردز وشارتات الـ What-If هنا]

    ![DAX Visuals](images/dashboard-main.png)

📊 4. Business Insights & Recommendations

ولأن الهدف الأساسي من أي داشبورد مالية هو خدمة متخذ القرار وتطوير البيزنس، هذه قراءة تحليلية لأهم المشكلات التي ظهرت في الأرقام، أثرها التجاري، والحلول الموصى بها:
المشكلة المكتشفة	الأثر على العمل والتجارة	الحل المقترح والموصى به
ارتفاع التكاليف (Costs) التشغيلية	تقليص صافي الأرباح وعرقلة النمو رغم زيادة حجم المبيعات الإجمالي.	مراجعة العقود اللوجستية والاعتماد على الأتمتة لخفض المصاريف الثابتة والمتغيرة.
ركود بعض المنتجات (No Sales)	تجميد السيولة النقدية وتكدس المخازن وتعرض المنتجات للتلف.	إطلاق حملات تصفية سريعة (Just-In-Time)، والاعتماد على نظام الشراء والتصنيع المستقبلي.
انخفاض متوسط الفاتورة (AOV)	ضعف الاستفادة القصوى من العميل الحالي (CAC) وارتفاع تكلفة الاستحواذ.	وضع حوافر شرائية مثل الشحن المجاني المشروط أو الخصومات التراكمية الذكية (Bundling).
تركز المبيعات جغرافياً (Revenue Concentration)	مخاطرة عالية للغاية في حال تأثر أو ركود هذه الأسواق الرئيسية.	توسيع الخطة التسويقية واستهداف المناطق الواعدة التي أظهرت المؤشرات ضعف التواجد فيها حالياً.

### 📊 لقطات من الداشبورد (Dashboard Snapshots)

هنا نظرة شاملة على أقسام التقرير المالي التفاعلي:

| :---: | :---: |
| ![Dashboard 1](https://raw.githubusercontent.com/MahmoudAtef-Data/Financial-P-L-Analysis-Dashboard/refs/heads/main/Revenue%20%26%20Margin.png) | ![Dashboard 2](https://raw.githubusercontent.com/MahmoudAtef-Data/Financial-P-L-Analysis-Dashboard/refs/heads/main/income%20statement.png)|

| :---: | :---: |
| ![Dashboard 3](https://raw.githubusercontent.com/MahmoudAtef-Data/Financial-P-L-Analysis-Dashboard/refs/heads/main/Financial%20Simulator.png) |![Dashboard 4](https://raw.githubusercontent.com/MahmoudAtef-Data/Financial-P-L-Analysis-Dashboard/refs/heads/main/REVENUE%20TOOLTIP.png) |

| :---: |
| ![Dashboard 5](https://raw.githubusercontent.com/MahmoudAtef-Data/Financial-P-L-Analysis-Dashboard/refs/heads/main/GM%20TOOLTIP.png) |



<img width="308" height="282" alt="GM TOOLTIP" src="https://github.com/user-attachments/assets/b5c5ed0f-a756-4ed6-9888-7e522ba60ab8" />
<img width="311" height="288" alt="REVENUE TOOLTIP" src="https://github.com/user-attachments/assets/5759b832-2555-4354-96a0-2b5bddc0f2ff" />
<img width="929" height="537" alt="Financial Simulator" src="https://github.com/user-attachments/assets/1fc500f4-7034-4b19-b428-84cd4d6b9f8a" />
<img width="929" height="537" alt="income statement" src="https://github.com/user-attachments/assets/bbfc2270-4531-40aa-b28f-ff1ba4e16deb" />
<img width="929" height="537" alt="Revenue   Margin" src="https://github.com/user-attachments/assets/6d0dae1d-0a10-43e9-8067-631584d92dc8" />









🛠️ Tech Stack & Tools
Category	Tools & Technologies
BI & Visualization	Power BI Desktop, DAX
Data Modeling	Star/Snowflake Schema, Relationships & Filter Propagation
Financial & Simulation	P&L Structure, What-If Parameters, Time Intelligence
Version Control	Git, GitHub
📬 Contact & Author

Mahmoud Atef

Junior Data Analyst & Business Intelligence Developer

    💼 LinkedIn: www.linkedin.com/in/mahmoudatefda

    📂 GitHub: MahmoudAtef-Data

⭐ لو المشروع عجبك، متنساش تدي Star للريبو وتشاركنا رأيك!
