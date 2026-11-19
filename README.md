# Superstore Sales Analysis

Sales analysis of a store chain (2015-2018): which categories, regions and years drive revenue.

## Question

Where do the store chain's sales come from, and how did they change over four years?

## Notebook

[superstore_sales_analysis.ipynb](https://github.com/Bilal-data/superstore-sales-analysis/blob/main/superstore_sales_analysis.ipynb), with outputs and a Findings cell at the end. The notebook reads the data from Google Drive; the data file is not in this repo.

## Data

Superstore Sales Dataset (Kaggle, uploaded by Rohit Sahoo), file `train.csv`: 9,800 rows and 18 columns, orders from 3 Jan 2015 to 30 Dec 2018. Each row is one product line inside an order, not one order. License: GPL 2, so I do not redistribute the file. It has revenue (Sales) only: no profit, discount or quantity columns.

https://www.kaggle.com/datasets/rohitsahoo/sales-forecasting

## Key findings

- Yearly sales: 479,856 (2015), 459,436 (2016), 600,193 (2017), 722,052 (2018). A 4% dip in 2016, then +31% and +20%.
- Technology leads with 36.6% of sales, then Furniture (32.2%) and Office Supplies (31.2%). Technology led in 3 of 4 years; Furniture was slightly ahead in 2016.
- Office Supplies has the most line items (5,909) but the lowest median item (27). Technology's mean (456) is pulled up by a few huge sales: the top 5 rows are about 9.2% of its sales.
- West (31.4%) and East (29.6%) make up about 61% of sales. South is last (17.2%) because it has the fewest line items (1,598), not cheaper ones.
- Growth 2015 to 2018: Office Supplies +61%, Technology +55%, Furniture +36%.
- 793 customers placed 4,922 orders. The top 20% of customers bring 48.3% of sales: concentrated, but far from the 80/20 rule.
- Sales peak late in the year: November, December and September together are about 43% of sales, and February is the lowest. The peak repeats every year, but the exact month changes (Sep 2015, Nov 2016, Dec 2017, Nov 2018). I can see the pattern but not its cause.
- Consumer brings 50.8% of sales, Corporate 30.4% and Home Office 18.8%. The ranking follows the number of line items, not the price: the median item is almost the same in the three segments (53 to 56). Consumer is the biggest because it has the most customers (409 of 793): a customer buys about the same in every segment.
- The segment mix is almost the same in all four regions (Consumer is 50% to 52% of each region's sales), so segments do not explain why the regions differ.
- Home Office leans toward Technology (42.9% of its sales, against 34.9% and 35.4% in the other two segments). Without the 5 largest Technology sales in each segment the gap is about half as big (35.8% against 32.0% and 31.0%), and without the 10 largest it is only 2.5 to 4.1 points (32.9% against 30.4% and 28.8%). Part of the lean came from a few large sales, and part remains. I ran no statistical test.

## Limitations

- Revenue only, no profit: a high-sales category may not be the most profitable one.
- Descriptive analysis only, with no statistical tests.
- I cannot say why regions or categories differ: there is no customer, store or quantity data.

## What I learned

- Parse dd/mm/yyyy dates with `dayfirst=True` and check the date range.
- A row can be a product line, not an order: row counts are not order counts.
- Mean vs median under skew, and always show the count next to it.
- Absolute growth and percentage growth can give different winners.
- `groupby`, `agg`, `pivot_table`, `nlargest` and a grouped bar chart.
- Reading a chart by eye is approximate: confirm with a table.

## Tools

Python, pandas, seaborn, matplotlib, Google Colab

---

## العربية

تحليل مبيعات سلسلة متاجر (2015-2018): أنهي فئات ومناطق وسنين بتجيب الإيراد.

### السؤال

المبيعات جاية منين، واتغيّرت إزاي على 4 سنين؟

### الداتا

Superstore Sales Dataset من Kaggle (رفعها Rohit Sahoo)، ملف `train.csv`: 9,800 صف و18 عمود، طلبات من 3 يناير 2015 لحد 30 ديسمبر 2018. كل صف هو منتج واحد جوه طلب، مش طلب كامل. الترخيص GPL 2، فمش بنشر الملف هنا. فيها الإيراد (Sales) بس: مفيش عمود ربح ولا خصم ولا كمية.

### أهم النتايج

- مبيعات السنين: 479,856 ثم 459,436 ثم 600,193 ثم 722,052. نزلت 4% في 2016 وبعدها زادت 31% و20%.
- Technology الأولى بحوالي 36.6% من المبيعات، وبعدها Furniture (32.2%) وOffice Supplies (31.2%). Technology تفوقت في 3 سنين من 4، وFurniture كانت أعلى شوية في 2016.
- Office Supplies أكتر بنود (5,909) بس وسيط البند فيها 27 بس. متوسط Technology (456) بتشده شوية مبيعات ضخمة: أعلى 5 صفوف حوالي 9.2% من مبيعاتها.
- West وEast مع بعض حوالي 61% من المبيعات. South الأخيرة (17.2%) لأن بنودها أقل (1,598)، مش لأن أسعارها أرخص.
- النمو من 2015 لـ 2018: Office Supplies +61%، وTechnology +55%، وFurniture +36%.
- 793 عميل عملوا 4,922 طلب. أعلى 20% من العملاء بيجيبوا 48.3% من المبيعات: تركيز واضح بس بعيد عن قاعدة 80/20.
- الموسم بيتركز في آخر السنة: نوفمبر وديسمبر وسبتمبر مع بعض حوالي 43% من المبيعات، وفبراير الأقل. القمة بتتكرر كل سنة بس الشهر بيتغير (سبتمبر 2015، نوفمبر 2016، ديسمبر 2017، نوفمبر 2018). شايف النمط بس مش عارف سببه.
- Consumer بيجيب حوالي 50.8% من المبيعات، وCorporate 30.4%، وHome Office 18.8%. الترتيب جاي من عدد البنود مش من السعر: البند العادي (الوسيط) تقريبًا واحد في التلات Segments (من 53 لـ 56).
- Consumer هو الأكبر لأن عنده أكتر عملاء (409 من 793): العميل بيشتري تقريبًا نفس القدر في كل Segment.
- تركيبة الـ Segments شبه ثابتة في المناطق الأربعة (Consumer بين 50% و52% من مبيعات كل منطقة)، يعني الـ Segments مش هي اللي بتفسّر ليه المناطق مختلفة.
- Home Office بيميل لـ Technology (42.9% من مبيعاته مقابل 34.9% و35.4% في الـ Segmentين التانيين). لما شلنا أكبر 5 عمليات بيع Technology في كل Segment، الفرق بقى حوالي النص (35.8% مقابل 32.0% و31.0%)، ولما شلنا أكبر 10 بقى 2.5 لـ 4.1 نقطة بس (32.9% مقابل 30.4% و28.8%). جزء من الميل كان من كام عملية كبيرة، وجزء فضل موجود. معملناش اختبار إحصائي.

### الحدود

- إيراد بس من غير ربح: الفئة الأعلى مبيعات مش لازم تكون الأعلى ربحًا.
- تحليل وصفي بس من غير اختبارات إحصائية.
- مش عارف ليه المناطق أو الفئات بتختلف: مفيش بيانات عن العملاء أو الفروع أو الكميات.

### اللي اتعلمته

- تحويل التواريخ dd/mm/yyyy بـ `dayfirst=True` ومراجعة المدى.
- الصف ممكن يكون بند مش طلب: عدد الصفوف مش عدد الطلبات.
- المتوسط والوسيط لما القيم مش متماثلة، وعرض العدد جنبهم.
- الزيادة بالرقم والزيادة بالنسبة ممكن يدّوا فايز مختلف.
- `groupby` و`agg` و`pivot_table` و`nlargest` ورسم أعمدة مجمّعة.
- قراءة الرسم بالعين تقريبية: لازم نتأكد من جدول.
