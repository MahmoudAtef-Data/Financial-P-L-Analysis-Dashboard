
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

![Dashboard 1](<Revenue & Margin.png>)

![Dashboard 2](<income statement.png>)

![Dashboard 3](<Financial Simulator.png>)

![Dashboard 4](<REVENUE TOOLTIP.png>)

![Dashboard 5](<GM TOOLTIP.png>)







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
