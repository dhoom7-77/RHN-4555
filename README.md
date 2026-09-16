---

# Comprehensive Project Report: Design, Hardware Integration, and Software Architecture of the Autonomous Robo-Car

## 1. Introduction & Project Overview

This document presents a detailed technical overview of our autonomous robo-car project. Unlike standard iterative modifications on off-the-shelf platforms, this project was conceived, engineered, and constructed entirely from scratch. The primary goal was to build a robust, self-correcting robotic system capable of precise navigation, accurate environmental sensing, and dynamic decision-making.

Throughout this report, we document the full development lifecycle—from raw structural architecture and component selection to code integration and system calibration. Accompanying this text are visual references, photographs of the fabricated car, hardware layout diagrams, and complete software algorithms illustrating the physical construction and functional control of the vehicle.

---

## 2. Mechanical Design & Structural Architecture (Built from Scratch)

### 2.1 Overcoming Initial Structural Limitations

In our initial engineering assessments, relying on pre-assembled chassis or minimal skeletal frames proved inadequate for our target performance metrics. Light structures introduced mechanical instability, chassis flex, and unpredictable inertia during sudden stops or turns. To overcome these constraints, we designed a custom structural frame tailored specifically to our electronic payload and weight distribution requirements.

### 2.2 Custom Frame Fabrication

* **Chassis Design:** Engineered from the ground up to ensure mechanical integrity, offering an optimal balance between structural rigidity and overall weight.
* **Component Placement:** Layout planning was executed to isolate high-noise power components (motors and drivers) from sensitive logic control units and environmental sensors.
* **Vibration Dampening:** Custom mounting points were integrated to minimize motor vibrations, directly improving the reading accuracy of onboard sensory units.

*(Refer to Figure 1.1 and Figure 1.2 in the visual documentation section for physical top-down and isometric views of the custom chassis assembly.)*

---

## 3. Hardware Configuration & Component Breakdown

To achieve full autonomy and stable drive characteristics, each hardware module was selected based on power efficiency, processing headroom, and operational compatibility.

### 3.1 Processing & Control Core

* **Microcontroller Unit (MCU):** Serves as the central nerve system of the robo-car, executing sensory read loops, processing control logic, and outputting PWM signals to the motor controllers in real time.

### 3.2 Actuation & Drive System

* **DC Gear Motors & Wheels:** Configured to deliver stable torque output for low-speed precision handling and smooth speed transitions.
* **H-Bridge Motor Driver Module:** Acts as the high-current interface between the microcontroller logic and the drive motors, enabling full bidirectional control (forward, reverse, braking) and precise speed variation via Pulse-Width Modulation (PWM).

### 3.3 Sensory & Environmental Perception System

* **Ultrasonic Distance Sensors:** Primary spatial perception units positioned strategically along the vehicle's perimeter. These sensors emit high-frequency sound waves to measure real-time proximity to surrounding obstacles and lateral boundaries.
* **Color / Optical Sensors:** Calibrated optical modules aimed at the ground surface to detect track boundaries, color-coded navigational markers, and operational zones.

### 3.4 Power Delivery Subsystem

* **Dedicated Power Rails:** To prevent logic resets caused by motor voltage dips, the power system is partitioned into logic power (microcontroller and sensors) and drive power (motor drivers and actuators), regulated through consistent voltage stabilization hardware.

---

## 4. Software Architecture & Embedded Code Base

The intelligence of the robo-car relies on custom-written embedded software algorithms designed to ensure low-latency processing and dynamic spatial adjustments. Rather than relying on simple reactive behaviors, the dedicated firmware codebase establishes a continuous feedback control loop.

### 4.1 System Logic & Algorithmic Workflow

1. **Sensory Polling Routine:** The microcontroller continuously runs background code loops to trigger ultrasonic transducers and optical sensors at precise millisecond intervals, generating an ongoing digital map of immediate obstacles.
2. **Real-Time Code Adjustments:** As distance data is processed by the internal algorithm, the code calculates off-center deviations. If the vehicle drifts too close to an boundary, the execution loop dynamically calculates corrective differential steering parameters.
3. **Motor Command Output:** The program outputs real-time Pulse-Width Modulation (PWM) signals directly to the motor driver channels, continuously balancing power between the left and right wheels to maintain an optimal trajectory.

### 4.2 Software Codebase Integration

*(Note: Full annotated C/C++ source code files, header configurations, pin assignment tables, and control loop logic diagrams are fully compiled and attached in Appendix B of this project repository).*

---

## 5. Testing, Calibration, and Performance Validation

The transition from theoretical design to practical execution involved extensive testing phases:

* **Sensor Noise Reduction & Calibration:** Early optical reads suffered from ambient lighting variance. Software filtering algorithms and physical shielding were implemented to stabilize line and color detection values.
* **Trajectory Correction Refinement:** Through iterative software parameter tuning, differential motor responses were calibrated to eliminate over-steering and oscillations during dynamic maneuvers.
* **Mechanical Stability Verification:** Building the chassis from scratch proved highly successful; structural rigidity eliminated chassis-shake completely, delivering consistent physical baseline conditions for sensor measurements.

---

## 6. Conclusion

By abandoning pre-built chassis kits and constructing our custom robo-car entirely from the ground up, we achieved complete hardware-software integration. The combination of a robust custom chassis, partitioned power delivery, multi-sensor environmental awareness, and dynamic closed-loop firmware resulted in a highly stable, precise, and fully autonomous vehicle platform.

*(Complete schematic drawings, high-resolution imagery of hardware wiring, visual diagrams, and the full embedded code repository are available in the accompanying technical appendices.)*

-- عربي --
إليك الترجمة الكاملة للتقرير باللغة العربية، مع الحفاظ على الأسلوب الأكاديمي التفصيلي، الصياغة الرسمية المكتظة بالمعلومات، والدقة التقنية:

---

# تقرير المشروع الشامل: التصميم، التكامل العتادي، والبيئة البرمجية للسيارة الروبوتية ذاتية القيادة

## 1. المقدمة ونظرة عامة على المشروع

يقدم هذا المستند نظرة عامة تقنية مفصلة لمشروع السيارة الروبوتية ذاتية القيادة الخاص بنا. بخلاف التعديلات التكرارية التقليدية التي تُجرى على المنصات والمهياكل الجاهزة، تم ابتكار هذا المشروع وتصميمه وهندسته وبنائه بالكامل من الصفر. تمثل الهدف الأساسي في بناء نظام روبوتي متين، قادر على تصحيح مساره ذاتياً، وإجراء الملاحة الدقيقة، الاستشعار البيئي الصارم، واتخاذ القرارات الديناميكية في الوقت الفعلي.

نقوم عبر أجزاء هذا التقرير بتوثيق دورة حياة التطوير الكاملة—بدءاً من البنية الهيكلية الأولية واختيار المكونات والقطع، وصولاً إلى التكامل البرمجي ومعايرة النظام. يرافق هذا النص توثيق بصري يتضمن صوراً فوتوغرافية للسيارة المصنعة، مخططات للتوزيع العتادي، وخوارزميات برمجية تشرح البناء المادي والتحكم الوظيفي للسيارة.

---

## 2. التصميم الميكانيكي والبنية الهيكلية (البناء من الصفر)

### 2.1 التغلب على القيود الهيكلية الأولية

في تقييماتنا الهندسية الأولية، تبين أن الاعتماد على الهياكل المجمعة مسبقاً أو الأطر الهيكلية الحد الأدنى غير كافٍ لتحقيق معايير الأداء المطلوبة. أدت الهياكل الخفيفة إلى عدم استقرار ميكانيكي، وانثناء في الشاسي، وقصور ذاتي غير محسوب أثناء التوقف المفاجئ أو الانعطاف. وللتغلب على هذه القيود، قمنا بتصميم هيكل بنيوي مخصص ومصمم خصيصاً لاستيعاب الحمولة الإلكترونية وتلبية متطلبات توزيع الوزن.

### 2.2 تصنيع الهيكل المخصص

* **تصميم الشاسي:** تم تصميمه هندسياً من الصفر لضمان السلامة الميكانيكية، مما يوفر توازناً مثالياً بين الصلابة الهيكلية والوزن الإجمالي.
* **توزيع المكونات:** تم تنفيذ تخطيط المكونات بعناية لعزل أجزاء الطاقة ذات الضوضاء العالية (المحركات والمشغلات) عن وحدات التحكم المنطقي والحساسات البيئية الحساسة.
* **إخماد الاهتزازات:** تم دمج نقاط تثبيت مخصصة لتقليل اهتزازات المحركات، مما أدى مباشرة إلى تحسين دقة قراءات وحدات الاستشعار المدمجة.

*(يرجى الرجوع إلى الشكل 1.1 والشكل 1.2 في قسم التوثيق البصري للاطلاع على المخططات العلوية والمنظورية لهيكل الشاسي المخصص).*

---

## 3. التكوين العتادي وتفصيل القطع المستخدمة

لتحقيق القيادة الذاتية الكاملة وخصائص القيادة المستقرة، تم اختيار كل وحدة عتادية بناءً على كفاءة استهلاك الطاقة، القدرة المعالجية الفائقة، والتوافق التشغيلي.

### 3.1 وحدة المعالجة والتحكم المركزية

* **وحدة المتحكم الدقيق (MCU):** تعمل بمثابة الجهاز العصبي المركزي للسيارة الروبوتية، حيث تقوم بتنفيذ دورات قراءة الحساسات، معالجة المنطق البرمجي، وإخراج إشارات تعديل عرض النبضة (PWM) إلى مشغلات المحركات في الوقت الفعلي.

### 3.2 نظام الدفع والحركة

* **محركات التروس (DC Gear Motors) والعجلات:** تم ضبطها لتوفير عزم دوران مستقر للتحكم الدقيق في السرعات المنخفضة وتحقيق انتقالات سلسة بين السرعات.
* **وحدة قيادة المحركات (H-Bridge Driver):** تعمل كواجهة ذات تيار عالٍ بين منطق المتحكم الدقيق ومحركات الدفع، مما يتيح التحكم الكامل ثنائي الاتجاه (إلى الأمام، إلى الخلف، والكبح) مع تغيير السرعة بدقة عبر تقنية تعديل عرض النبضة (PWM).

### 3.3 نظام الاستشعار والإدراك البيئي

* **حساسات المسافة الموجات فوق الصوتية (Ultrasonic):** تمثل وحدات الإدراك المكاني الأساسية والموضوعة إستراتيجياً على طول محيط السيارة. تقوم هذه الحساسات بإرسال موجات صوتية عالية التردد لقياس القرب الفعلي من العوائق والمحيط الجانبي في الوقت الفعلي.
* **حساسات الألوان والضوء (Color / Optical Sensors):** وحدات بصرية تم معايرتها وتوجيهها نحو سطح الأرض للكشف عن حدود المسار، العلامات الملاحية الملونة، ومناطق العمليات.

### 3.4 نظام توزيع الطاقة الفرعي

* **خطوط تغذية مخصصة:** لمنع إعادة تشغيل المتحكم (Logic Resets) الناتجة عن هبوط الجهد عند تشغيل المحركات، تم تقسيم نظام الطاقة إلى طاقة للمنطق (المتحكم والحساسات) وطاقة للدفع (مشغلات المحركات والمحركات نفسها)، مع تنظيمها عبر منظمات جهد مستقرة.

---

## 4. البنية البرمجية وقاعدة الأكواد المدمجة

تعتمد ذكاء السيارة الروبوتية على خوارزميات برمجية مدمجة مكتوبة خصيصاً لضمان المعالجة منخفضة التكلفة للوقت (Low-Latency) وإجراء التعديلات المكانية الديناميكية. بدلاً من الاعتماد على ردود الفعل البسيطة، تؤسس البيئة البرمجية حلقة تحكم واستجابة مستمرة.

### 4.1 المنطق البرمجي وسلسلة تدفق الخوارزميات

1. **روتين قراءة الحساسات:** يُمضي المتحكم الدقيق أكواداً برمجية تعمل في الخلفية باستمرار لتشغيل الحساسات فوق الصوتية والبصرية في فترات زمنية دقيقة بالمللي ثانية، مما ينشئ خريطة رقمية متجددة للعوائق القريبة.
2. **التعديلات البرمجية في الوقت الفعلي:** أثناء معالجة بيانات المسافة بواسطة الخوارزمية الداخلية، يحسب الكود الانحرافات عن المركز. إذا اقتربت السيارة من الحدود الجانبية، تحسب حلقة التنفيذ ديناميكياً معايير التوجيه التفاضلي لتصحيح المسار.
3. **أوامر مخرجات المحرك:** يقوم البرنامج بإرسال إشارات تعديل عرض النبضة (PWM) في الوقت الفعلي مباشرة إلى قنوات مشغل المحرك، مما يوازن الطاقة باستمرار بين العجلات اليسرى واليمنى للحفاظ على المسار الأمثل.

### 4.2 تكامل الأكواد والبرمجيات

*(ملاحظة: تم تجميع الملفات البرمجية الكاملة والمكتوبة بلغة C/C++، مع جداول تعيين الدبابيس "Pins"، ومخططات حلقة التحكم وتحليل الخوارزميات وإرفاقها بالكامل في الملحق "ب" من هذا المشروع).*

---

## 5. الاختبار، المعايرة، والتحقق من الأداء

تضمنت مرحلة الانتقال من التصميم النظرية إلى التنفيذ العملي مراحل اختبار مكثفة:

* **تقليل ضوضاء الحساسات والمعايرة:** عانت القراءات البصرية الأولية من التباين في الإضاءة المحيطة. تم تطبيق خوارزميات تصفية برمجية مع دروع حماية مادية لتثبيت قراءات تتبع الخطوط والألوان.
* **تحسين تصحيح المسار:** من خلال الضبط التكراري للمعلمات البرمجية، تم ضبط استجابة المحركات التفاضلية للقضاء على الانعطاف الزائد (Over-steering) والتأرجح أثناء المناورات الديناميكية.
* **التحقق من الاستقرار الميكانيكي:** أثبت بناء الشاسي من الصفر نجاحاً كبيراً؛ حيث قضت الصلابة الهيكلية على اهتزازات السيارة تماماً، مما وفر ظروفاً مرجعية مادية مستقرة لقراءات الحساسات.

---

## 6. الخاتمة

من خلال التخلي عن أطقم الهياكل الجاهزة وبناء سيارتنا الروبوتية المخصصة بالكامل من الصفر، حققنا تكاملاً تاماً بين العتاد والبرمجيات. أدى الجمع بين الشاسي المخصص والمتين، توزيع الطاقة المقسم، الإدراك البيئي متعدد الحساسات، والبرمجيات المدمجة ذات التغذية الراجعة الديناميكية إلى إنشاء منصة مركبة ذاتية القيادة تتميز بالاستقرار العالي، الدقة، والعمل الذاتي الكامل.

*(المخططات الهندسية الكاملة، الصور عالية الدقة لتوصيلات العتاد، المخططات البصرية، ومستودع الأكواد المدمجة الكاملة متوفرة في الملاحق التقنية المرفقة).*
