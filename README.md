<!DOCTYPE html>
<html lang="he" dir="rtl">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>מבדק אקרדיטציה - מרכז שניידר לרפואת ילדים</title>
    <link href="https://fonts.googleapis.com/css2?family=Heebo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
    <style>
        :root {
            --schneider-blue: #005691;
            --schneider-light-blue: #00a8e8;
            --schneider-teal: #00b4d8;
            --schneider-dark: #1e293b;
            --bg-light: #f8fafc;
            --card-bg: #ffffff;
            --accent-red: #ef4444;
            --accent-green: #10b981;
            --accent-purple: #8b5cf6;
            --accent-pink: #ec4899;
            --accent-yellow: #f59e0b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Heebo', sans-serif;
        }

        body {
            background-color: var(--bg-light);
            color: var(--schneider-dark);
            line-height: 1.6;
            padding-bottom: 50px;
        }

        header {
            background: linear-gradient(135deg, var(--schneider-blue), var(--schneider-teal));
            color: white;
            padding: 20px 15px;
            text-align: center;
            box-shadow: 0 4px 12px rgba(0,0,0,0.15);
            position: sticky;
            top: 0;
            z-index: 1000;
        }

        header h1 {
            font-size: 1.6rem;
            font-weight: 900;
        }

        header p {
            font-size: 0.95rem;
            opacity: 0.9;
        }

        .quick-dial-bar {
            display: flex;
            overflow-x: auto;
            gap: 10px;
            padding: 12px 15px;
            background: #e0f2fe;
            border-bottom: 2px solid #bae6fd;
        }

        .dial-chip {
            background: white;
            border: 1px solid #7dd3fc;
            padding: 6px 12px;
            border-radius: 20px;
            white-space: nowrap;
            font-size: 0.85rem;
            font-weight: 700;
            color: var(--schneider-blue);
            box-shadow: 0 2px 4px rgba(0,0,0,0.05);
            display: flex;
            align-items: center;
            gap: 5px;
        }

        .dial-chip span.num {
            color: var(--accent-red);
            font-size: 0.95rem;
        }

        .container {
            max-width: 900px;
            margin: 15px auto;
            padding: 0 15px;
        }

        .search-box {
            position: relative;
            margin-bottom: 20px;
        }

        .search-box input {
            width: 100%;
            padding: 14px 45px 14px 15px;
            border-radius: 30px;
            border: 2px solid #cbd5e1;
            font-size: 1rem;
            outline: none;
            transition: all 0.3s;
        }

        .search-box input:focus {
            border-color: var(--schneider-light-blue);
            box-shadow: 0 0 0 4px rgba(0, 168, 232, 0.15);
        }

        .search-box::before {
            content: "🔍";
            position: absolute;
            right: 15px;
            top: 50%;
            transform: translateY(-50%);
            font-size: 1.2rem;
        }

        .nav-tabs {
            display: flex;
            gap: 8px;
            margin-bottom: 20px;
            overflow-x: auto;
            padding-bottom: 5px;
        }

        .tab-btn {
            flex: 1;
            min-width: 110px;
            padding: 10px 12px;
            background: white;
            border: 1px solid #cbd5e1;
            border-radius: 12px;
            font-weight: 700;
            font-size: 0.88rem;
            cursor: pointer;
            text-align: center;
            transition: all 0.2s;
            color: #64748b;
        }

        .tab-btn.active {
            background: var(--schneider-blue);
            color: white;
            border-color: var(--schneider-blue);
            box-shadow: 0 4px 8px rgba(0, 86, 145, 0.2);
        }

        .tab-content {
            display: none;
        }

        .tab-content.active {
            display: block;
        }

        .card {
            background: var(--card-bg);
            border-radius: 16px;
            padding: 18px;
            margin-bottom: 15px;
            box-shadow: 0 2px 8px rgba(0,0,0,0.06);
            border-right: 6px solid var(--schneider-teal);
        }

        .card.red-border { border-right-color: var(--accent-red); }
        .card.purple-border { border-right-color: var(--accent-purple); }
        .card.green-border { border-right-color: var(--accent-green); }
        .card.yellow-border { border-right-color: var(--accent-yellow); }

        .card h3 {
            font-size: 1.15rem;
            margin-bottom: 10px;
            color: var(--schneider-blue);
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        .badge {
            font-size: 0.75rem;
            padding: 3px 8px;
            border-radius: 6px;
            background: #f1f5f9;
            color: #475569;
            font-weight: 600;
        }

        ul, ol {
            padding-right: 20px;
            margin-top: 8px;
        }

        li {
            margin-bottom: 6px;
            font-size: 0.95rem;
        }

        .highlight-box {
            background: #fff1f2;
            border: 1px solid #fecdd3;
            color: #9f1239;
            padding: 10px 12px;
            border-radius: 10px;
            font-weight: 600;
            margin-top: 10px;
            font-size: 0.9rem;
        }

        .wristbands-grid {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(240px, 1fr));
            gap: 10px;
            margin-top: 10px;
        }

        .wb-item {
            padding: 10px;
            border-radius: 10px;
            font-size: 0.88rem;
            font-weight: 600;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .wb-purple { background: #f3e8ff; color: #6b21a8; border: 1px solid #d8b4fe; }
        .wb-blue { background: #e0f2fe; color: #0369a1; border: 1px solid #bae6fd; }
        .wb-white { background: #f8fafc; color: #334155; border: 1px solid #cbd5e1; }
        .wb-red { background: #fee2e2; color: #991b1b; border: 1px solid #fca5a5; }
        .wb-green { background: #dcfce7; color: #166534; border: 1px solid #86efac; }
        .wb-pink { background: #fce7f3; color: #9d174d; border: 1px solid #fbcfe8; }

        .quiz-card {
            background: white;
            border-radius: 16px;
            padding: 20px;
            margin-bottom: 15px;
            border: 1px solid #e2e8f0;
            box-shadow: 0 2px 6px rgba(0,0,0,0.04);
        }

        .quiz-q {
            font-weight: 700;
            font-size: 1.05rem;
            color: var(--schneider-blue);
            margin-bottom: 10px;
        }

        .quiz-a {
            display: none;
            background: #f0fdf4;
            border: 1px solid #bbf7d0;
            padding: 12px;
            border-radius: 10px;
            color: #166534;
            font-weight: 600;
            font-size: 0.95rem;
            margin-top: 10px;
        }

        .btn-toggle {
            background: var(--schneider-light-blue);
            color: white;
            border: none;
            padding: 8px 16px;
            border-radius: 8px;
            font-weight: 700;
            cursor: pointer;
            font-size: 0.85rem;
        }

        .checklist-item {
            display: flex;
            align-items: center;
            gap: 12px;
            padding: 12px;
            background: white;
            border-radius: 10px;
            margin-bottom: 8px;
            border: 1px solid #e2e8f0;
        }

        .checklist-item input {
            width: 20px;
            height: 20px;
            accent-color: var(--schneider-blue);
            cursor: pointer;
        }

        .checklist-item label {
            cursor: pointer;
            font-size: 0.95rem;
            font-weight: 600;
        }
    </style>
</head>
<body>

    <header>
        <h1>מרכז שניידר לרפואת ילדים</h1>
        <p>מדריך הכנה אינטראקטיבי למבדק האקרדיטציה</p>
    </header>

    <div class="quick-dial-bar">
        <div class="dial-chip">📞 החייאה: <span class="num">2222</span></div>
        <div class="dial-chip">📞 טפ"נ: <span class="num">3000</span></div>
        <div class="dial-chip">🔥 שריפה/ביטחון: <span class="num">3232</span></div>
        <div class="dial-chip">🌐 תרגום: <span class="num">*5144</span></div>
        <div class="dial-chip">💻 סייבר: <span class="num">4321</span></div>
    </div>

    <div class="container">
        <div class="search-box">
            <input type="text" id="searchInput" placeholder="חפשי נוהל, צמיד, קוד חירום או מילת מפתח..." onkeyup="filterContent()">
        </div>

        <div class="nav-tabs">
            <button class="tab-btn active" onclick="switchTab('tab1')">📌 זיהוי וזיהומים</button>
            <button class="tab-btn" onclick="switchTab('tab2')">🚨 חירום ובטיחות</button>
            <button class="tab-btn" onclick="switchTab('tab3')">🛡️ רשומה וסייבר</button>
            <button class="tab-btn" onclick="switchTab('tab4')">🧠 סימולטור סוקר</button>
            <button class="tab-btn" onclick="switchTab('tab5')">✅ צ'ק-ליסט</button>
        </div>

        <!-- TAB 1: זיהוי ומניעת זיהומים -->
        <div id="tab1" class="tab-content active">
            
            <div class="card">
                <h3>זיהוי מטופל <span class="badge">IPSG 01.00</span></h3>
                <p><strong>כיצד מזהים מטופל?</strong> באמצעות 2 אמצעים יזומים:</p>
                <ol>
                    <li>שם מלא</li>
                    <li>מספר תעודת זהות</li>
                </ol>
                <p style="margin-top:6px;">אם ת"ז אינה ידועה: שם מלא + מזהה נוסף (שם האב או תאריך לידה). בתיירים/עובדים זרים: מספר מזהה במדבקה.</p>
                <div class="highlight-box">
                    🚨 חובה: אין להקריא לצוות/מטופל/הורה! יש לבקש מהם לומר את הפרטים באופן יזום ולבצע השוואה לצמיד/רשומה.
                </div>
            </div>

            <div class="card purple-border">
                <h3>סוגי צמידים/ידונים בביה"ח</h3>
                <div class="wristbands-grid">
                    <div class="wb-item wb-purple">🟣 סגול - זיהוי מטופלים במלר"ד</div>
                    <div class="wb-item wb-blue">🔵 כחול - זיהוי במרפאות/מכונים</div>
                    <div class="wb-item wb-white">⚪ לבן - מאושפזים ללא רגישות לתרופות</div>
                    <div class="wb-item wb-red">🔴 אדום - רגישות ידועה לתרופה</div>
                    <div class="wb-item wb-green">🟢 ירוק - רגישות למזון (נענד בנוסף, כותבים את סוג הרגישות)</div>
                    <div class="wb-item wb-pink">🌸 ורוד - סימון גפה בסיכון</div>
                </div>
            </div>

            <div class="card green-border">
                <h3>היגיינת ידיים <span class="badge">IPSG 05.00</span></h3>
                <p><strong>5 הרגעים להיגיינת ידיים:</strong></p>
                <ol>
                    <li>לפני מגע במטופל</li>
                    <li>לפני מגע אספטי</li>
                    <li>לאחר סכנת חשיפה לנוזלי גוף</li>
                    <li>לאחר מגע במטופל</li>
                    <li>לאחר מגע בסביבת המטופל</li>
                </ol>
                <p style="margin-top:10px;"><strong>איך ומתי?</strong></p>
                <ul>
                    <li><strong>ספטול (אלכוהול):</strong> חיטוי מהיר כשהידיים נקיות למראית עין.</li>
                    <li><strong>מים וסבון אנטימיקרוביאלי (ספטל סקראב):</strong> חובה בלכלוך נראה לעין, ביקור בשירותים, טיפול במטופל משלשל או אבחנת <em>C. difficile</em>.</li>
                </ul>
                <div class="highlight-box">
                    💅 ציפורניים ותכשיטים: ללא ציפורניים מלאכותיות, אורך עד 0.5 ס"מ, ללא לק שבור. איסור טבעות (פרט לטבעת נישואין חלקים). כפפות אינן תחליף להיגיינת ידיים!
                </div>
            </div>

            <div class="card red-border">
                <h3>סוגי בידודים וסדר PPE</h3>
                <p><strong>סדר לבישת ציוד מגן:</strong> חלוק ⬅️ מסכה ⬅️ משקפיים/מגן פנים ⬅️ כפפות</p>
                <p><strong>סדר הסרת ציוד מגן:</strong> כפפות ⬅️ משקפיים/מגן פנים ⬅️ חלוק ⬅️ מסכה (+היגיינת ידיים)</p>
                <hr style="margin: 10px 0;">
                <ul>
                    <li>🔴 <strong>בידוד מגע (אדום):</strong> MRSA, VRE, CRE, C. difficile, Acinetobacter, RSV. (חובה חלוק + כפפות. ב-C. diff חובה מים וסבון!).</li>
                    <li>🟢 <strong>בידוד טיפתי (ירוק):</strong> שפעת (Influenza), שעלת (Pertussis), חזרת (Mumps), מנינגוקוקוס. (מסכה כירורגית בכניסה).</li>
                    <li>🔵 <strong>בידוד אוויר (כחול):</strong> שחפת, חצבת, אבעבועות רוח. (חדר תת-לחץ, דלת סגורה, מסכת N95).</li>
                </ul>
            </div>

            <div class="card yellow-border">
                <h3>מקרר חלב אם - אחסון וסימון</h3>
                <ul>
                    <li>מאוחסן בכלי חד-פעמי ייעודי המסופק על ידי האחות.</li>
                    <li><strong>מדבקה חובה:</strong> מדבקת פרטי מטופל + תאריך ושעת השאיבה + חתימת האחות.</li>
                    <li>ממוקם בסלסלה אישית במדפים התחתונים של מקרר הפורמולה במחלקה.</li>
                </ul>
            </div>

        </div>

        <!-- TAB 2: חירום ובטיחות -->
        <div id="tab2" class="tab-content">
            
            <div class="card red-border">
                <h3>הפעלת קוד החייאה / חירום</h3>
                <ol>
                    <li>חייגו <strong>2222</strong>.</li>
                    <li>המתינו 2 שניות והגידו פעמיים: <br><em>"החייאה במחלקה ___ | בניין ___ | קומה ___ | חדר ___"</em></li>
                    <li>חייגו בנוסף לטיפול נמרץ: <strong>3000</strong> (ובמענה האנושי חזרו על המיקום).</li>
                </ol>
            </div>

            <div class="card">
                <h3>שריפה - סדר פעולות ד.ח.י.פ</h3>
                <ul>
                    <li><strong>ד - דיווח:</strong> מיידי למוקד ביטחון <strong>3232</strong> (מיקום מדויק: בניין, קומה, מחלקה, חדר) או לחצן אש.</li>
                    <li><strong>ח - חילוץ:</strong> חילוץ אנשים בסכנה מיידית והרחקת קהל.</li>
                    <li><strong>י - ינסה לכבות:</strong> בבטחה באמצעות מטף (איסור שימוש במים!).</li>
                    <li><strong>פ - פינוי:</strong> פינוי מטופלים וצוות לפי הנחיות.</li>
                </ul>
            </div>

            <div class="card yellow-border">
                <h3>חשיפה לדם ולנוזלי גוף (נחשפת?)</h3>
                <ol>
                    <li><strong>ניקוי הפצע:</strong> מים זורמים וסבון סקראב (עיניים: שטיפה במים זורמים בלבד).</li>
                    <li><strong>דיווח:</strong> מיידי לממונה הישיר.</li>
                    <li><strong>פנייה:</strong> מיידית למלר"ד בבילינסון לקבלת טיפול ראשוני.</li>
                    <li><strong>טופס 250:</strong> העברת טופס 250 ממשאבי אנוש למלר"ד.</li>
                    <li><strong>דיווח המשכי:</strong> לאחות מרפאת עובדים / יחידה למניעת זיהומים.</li>
                </ol>
            </div>

            <div class="card purple-border">
                <h3>תוצאה קריטית בטלפון</h3>
                <ul>
                    <li><strong>מי מוסמך לקבל?</strong> רופא/ה או אח/ות.</li>
                    <li><strong>תוצאה בפתולוגיה או בדימות:</strong> תימסר לרופא/ה בלבד!</li>
                </ul>
            </div>

        </div>

        <!-- TAB 3: רשומה וסייבר -->
        <div id="tab3" class="tab-content">
            
            <div class="card">
                <h3>רשומה רפואית (MOI) - דגשי תיעוד</h3>
                <ul>
                    <li><strong>איסור קיצורים:</strong> מותר להשתמש רק בקיצורים מאושרים. <em>חל איסור מוחלט על קיצורים ב:</em> מכתב שחרור/פטירה, טפסי הסכמה, הנחיות להמשך טיפול וסיכום מחלה.</li>
                    <li><strong>פונקציית העתק-הדבק:</strong> מותר להעתיק רק מידע שנבדק ורלוונטי, תוך ציון המקור. אין להציג מידע מועתק כאילו נכתב בזמן אמת.</li>
                    <li><strong>איכות התיעוד:</strong> מדויק, מלא, ברור, בזמן, משקף תוכנית טיפול ומטרות.</li>
                </ul>
            </div>

            <div class="card red-border">
                <h3>הגנת מידע וסייבר (HCT)</h3>
                <ul>
                    <li><strong>הרשאות:</strong> גישה לרשומה רק למטופלים שבטיפולך הישיר. איסור כניסה לרשומות של קרובים/עצמך.</li>
                    <li><strong>אבטחה:</strong> איסור שימוש בסיסמת עובד אחר. נעילת מחשב בכל יציאה מהעמדה.</li>
                    <li><strong>איסור וואטסאפ/מייל פרטי:</strong> אין להעביר מידע רפואי או תמונות במייל/וואטסאפ פרטי.</li>
                    <li><strong>מייל חשוד:</strong> לדווח בלחיצה על כפתור "דיווח מייל חשוד".</li>
                    <li><strong>חשד לאירוע סייבר:</strong> לדווח למוקד <strong>4321</strong> (או 077-707207) ולנתק כבל רשת. <em>איסור כיבוי המחשב!</em></li>
                </ul>
            </div>

            <div class="card green-border">
                <h3>נגישות, שפות וכיבוד תרבותי</h3>
                <ul>
                    <li><strong>תרגום טלפוני "קול לבריאות":</strong> חייגו <strong>*5144</strong> (ערבית, רוסית, אמהרית, טיגרית, צרפתית). א'-ה' 08:00-20:00, ו' 08:00-13:00.</li>
                    <li><strong>ייעוץ דת/רב ביה"ח:</strong> הרב אשר לוי (050-4205574 / 03-9253971).</li>
                    <li>שפת הסימנים ותרגום נוסף זמינים בפורטל שניידר.</li>
                </ul>
            </div>

        </div>

        <!-- TAB 4: סימולטור סוקר -->
        <div id="tab4" class="tab-content">
            
            <div class="quiz-card">
                <div class="quiz-q">❓ שאלה: הסוקר שואל: "איך את מזהה מטופל לפני מתן ייעוץ תזונתי או הזנה?"</div>
                <button class="btn-toggle" onclick="toggleAnswer('q1')">הצג תשובה מומלצת</button>
                <div id="q1" class="quiz-a">
                    "אני מבקשת מההורה/המטופל לומר באופן יזום שם מלא ומספר תעודת זהות, ומשווה אותם לצמיד הזיהוי ולרשומה הרפואית. אני לעולם לא מקריאה את הפרטים!"
                </div>
            </div>

            <div class="quiz-card">
                <div class="quiz-q">❓ שאלה: "מה משמעות צמיד ירוק על יד של ילד במחלקה?"</div>
                <button class="btn-toggle" onclick="toggleAnswer('q2')">הצג תשובה מומלצת</button>
                <div id="q2" class="quiz-a">
                    "צמיד ירוק מסמן רגישות למזון. הוא נענד בנוסף לצמיד הזיהוי הרגיל (או האדום), ורשום עליו סוג הרגישות למזון."
                </div>
            </div>

            <div class="quiz-card">
                <div class="quiz-q">❓ שאלה: "איך מדווחים על אירוע החייאה במחלקה?"</div>
                <button class="btn-toggle" onclick="toggleAnswer('q3')">הצג תשובה מומלצת</button>
                <div id="q3" class="quiz-a">
                    "מחייגים 2222, ממתינים 2 שניות ואומרים פעמיים: החייאה במחלקה, בניין, קומה וחדר. בנוסף מחייגים 3000 לטיפול נמרץ ומדווחים אנושית."
                </div>
            </div>

            <div class="quiz-card">
                <div class="quiz-q">❓ שאלה: "מה את עושה אם קיבלת מייל שנראה חשוד או בעל קובץ מוזר?"</div>
                <button class="btn-toggle" onclick="toggleAnswer('q4')">הצג תשובה מומלצת</button>
                <div id="q4" class="quiz-a">
                    "לא פותחת קבצים או קישורים, ולוחצת על כפתור 'דיווח מייל חשוד' באאוטלוק או מדווחת למוקד 4321."
                </div>
            </div>

            <div class="quiz-card">
                <div class="quiz-q">❓ שאלה: "מתי חובה לרחץ ידיים במים וסבון ולא להסתפק בספטול?"</div>
                <button class="btn-toggle" onclick="toggleAnswer('q5')">הצג תשובה מומלצת</button>
                <div id="q5" class="quiz-a">
                    "כשרואים לכלוך בעין, אחרי ביקור בשירותים, בטיפול במטופל משלשל, או במטופל עם אבחנה/חשד ל-C. difficile."
                </div>
            </div>

        </div>

        <!-- TAB 5: צ'ק-ליסט -->
        <div id="tab5" class="tab-content">
            <div class="card">
                <h3>צ'ק-ליסט מוכנות בוקר למחלקה</h3>
                <p style="margin-bottom: 12px; font-size: 0.9rem;">סמני V על הסעיפים שבדקת לפני תחילת העבודה:</p>

                <div class="checklist-item">
                    <input type="checkbox" id="c1">
                    <label for="c1">וידאתי שצמיד הזיהוי של המטופל תואם לתיק הרפואי</label>
                </div>

                <div class="checklist-item">
                    <input type="checkbox" id="c2">
                    <label for="c2">בדקתי אם למטופל יש רגישות מזון (צמיד ירוק) או רגישות לתרופות (צמיד אדום)</label>
                </div>

                <div class="checklist-item">
                    <input type="checkbox" id="c3">
                    <label for="c3">שמרתי על היגיינת ידיים לפני ואחרי כניסה לחדר המטופל</label>
                </div>

                <div class="checklist-item">
                    <input type="checkbox" id="c4">
                    <label for="c4">בדקתי שחלב אם במקרר הפורמולה מסומן עם מדבקה, תאריך, שעה וחתימת אחות</label>
                </div>

                <div class="checklist-item">
                    <input type="checkbox" id="c5">
                    <label for="c5">נעלתי את עמדת המחשב בעת יציאה מהחדר/המחלקה</label>
                </div>

                <div class="checklist-item">
                    <input type="checkbox" id="c6">
                    <label for="c6">וידאתי שאין קיצורים לא מאושרים בסיכומי השחרור/הערכות</label>
                </div>
            </div>
        </div>

    </div>

    <script>
        function switchTab(tabId) {
            document.querySelectorAll('.tab-content').forEach(el => el.classList.remove('active'));
            document.querySelectorAll('.tab-btn').forEach(el => el.classList.remove('active'));
            
            document.getElementById(tabId).classList.add('active');
            event.currentTarget.classList.add('active');
        }

        function toggleAnswer(id) {
            const ans = document.getElementById(id);
            if (ans.style.display === "block") {
                ans.style.display = "none";
            } else {
                ans.style.display = "block";
            }
        }

        function filterContent() {
            const query = document.getElementById('searchInput').value.toLowerCase();
            const cards = document.querySelectorAll('.card, .quiz-card');

            cards.forEach(card => {
                const text = card.innerText.toLowerCase();
                if (text.includes(query)) {
                    card.style.display = 'block';
                } else {
                    card.style.display = 'none';
                }
            });
        }
    </script>
</body>
</html>
