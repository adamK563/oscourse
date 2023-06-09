# Operating Systems Exam Preparation

This repository contains my preparation materials for the "Operating Systems" exam. The exam covers various topics related to operating systems, including process management, memory management, file systems, and synchronization.

## Study Plan
## - Week 0:
## הקדמה:

### רכבי מערכת מחשב:
1. חומרה - מעבד, זיכרון, התקני קלט פלט
2. מערכת הפעלה - מ"ע 
3. תוכנית משתמש - קומפיילר, סביבת פיתוח וכו'
4. משתמשים - USER - בני אדם ומחשבים אחרים
## - Week 1:
#### What an OS
An operating system (OS) is system software that manages computer hardware and software resources.

### תפקידי מ"ע:
1. קובעת מתי ואיך תרוץ תוכנית
2. מנהלת התקני קלט פלט
3. גרעין OS Kernel התוכנית הראשית של מ"ע

#### OS kernel
The kernel is a computer program at the core of a computer's operating system and generally has complete control over everything in the system.

### תפקידי בגרעין:
1. אחראי על התזמון של תהליכים
2. אחראי על טיפול בקשות (הפעלה של התקן חומרה)
- יש מגבלת זמן לכל תוכנית.
- פסיקה - interrupt - סיגנל למ"ע להתיחס
- 1. פיסקת תוכנה - TRAP
- 2. פסירת חומרה - פשוט INTERRUPT 

### מה צריך להיות במ"ע:
1. מ"ע צריך לדעת לתקשר עם התקני חומרה (DEVICE DRIVER) 
2. ניהול זכרון - הקצעת זיכרון באופן יעיל
3. תזמון - בעזרת ה scheduler (המתזמן) מתי כל תכנית תרוץ
4. מקום בדיסק בשם Spool, הספול שומר תהליכים איטים לרכיבי חומרה איטים (מדפסת) spooling


#### Categories of OSes:

### Time sharing systems:
מחשבים של פעם - תוכניות לא רצות במקביל באופן רציף - כלומר מתבצעת החלפה מהירה בין התוכניות על אותו מעבד 
### Multiprogramming systems:
- מ"ע יודעת להריץ כמה תוכניות "במקביל" (למדויק אבל כך זה מרגיש)
- לא נרגיש כל פעם רצה תוכנית אחרת אלא הכל פועל פעופן מקביל ורציף


#### Parallel systems: - מערכות מסוג עיבוד מקבילי
### סוגים של עיבוד מקבילי:
1. עיבוד מקבילי סמטרי - SMP - כל המעבדים שווי מעמד אין master (מחשבים רגילים)
2. עיבוד מקבילי אי סמטרי - קיים מעבד master אשר שולט משאר (מחשב על)

- Time sharing systems are Parallel systems
- Multiprogramming systems are Parallel systems

- Tightly coupled systems - חולקות זיכרון ושעון, תפוקה גבוה(*)

תפוקה - troughput
- Loosly coupled system - in Distributed systems a computer runs it
- מערכת מבוזרת - Distrebuted system - מערכת של כמה מחשבים 
- שיתוף משאבים
- תפוקה
- אמינות - עם מחשב אחד נופל המערכת ממשיכה לפעול

- Real-time systems
 ### סוגים של מערכות זמן אמת:
 1. Hard real-time systems: 
 A hard real-time system has absolute deadlines, and if those allotted time spans are missed, a system failure will occur.
 - example: Iron Dome (97%+ success rate)
 
 2. Soft real-time systems, the system continues to function even if missing a deadline, but with undesirable lower quality of output.
 - example: Smart fridge (We say thank if somehting smart happens)

## - Week 2:
####  Storage:

### סוגי זכרון במחשב:
1. זקרון מהיר - RAM - זכרון נמחק לאחר RESET
2. שטח דיסק - זיכרון משני - דיסק קשיח - HD - Hard disk
3. קאש - cache - זכרון זמני - נועד לשמור נתונים של ה CPU ותוכנות או תהליכים
4. אגרי מעבד - hardware register - תוכנות מחשב כותבות ומשתמשות בזכרון הזה כדי לתקשר עם המעבד

### HD מגנטי
- צלחות מגנטיות - מסתובבות על ציר (קומות שונות) במקביל
- משטח מגנות - צד אחד בצלחת מגנות (מלמלע ויש גם למטה)
- ראש קורא כותב - ידית שקוראת 
- סקטור - יחידה שנתן לקרוא
- טראק - אוסף של סקטורים ברדיואוס של המשטח מגנות
- צלינדר - אוסף כל הטראקס (מכל הצלחות) שבאותו הרדיאוס


#### Interrupts:

## הקדמה:
- חיבור פיזי שכל התקני חומרה מחוברים אליו - BUS 
- לכל התקן חומרה יש בקר משלו (controller)
- הבקר (controller) - מקשר בין הרכיב חומרה למעבד
- קיימים שני התקני חומרה: מהיר ואיטי
- התקן חומרה איטי: מדפסת
- התקן חומרה מהיר: מסך, מקלדת, עכבר

### בקר Controller

- המעבד לא מדבר בצורה ישירה עם התקן חומרה
- המעבד מדבר עם הבקר כדי לקבל נתונים על הרכיב חומרה
- למעבד יש Driver לכל בקר כזה בשביל תקשורת
- לכל בקר יש buffer (זכרון קטן)

נקודות חשובות:
- התקני קלט פלט והמעבד עובדים במקביל
- לכל התקן חומרה יש בקר משלו
- לכל בקר יש buffer פנימי
- בקר מעדכן את המעבד על שינוי באמצאות פסיקה

### פסיקה:
- לאחר קבל פסיקה המעבד מריץ (Interrupt service routine) ISR

- שה ISR זה פונקציה לטיפול פסיקות.
- פיסקה בנוי מ8 ביטים וגם כך המעבד יודע לזעות מאיזה סוג הפיסקה (לפי ה8 ביטים)

- ה Interupt Vector - מכיל את כל הפסאות האפשריות שיש למערכת הפעלה בסדר לפי 8 הביטים
- הוקטור שמור בRAM המחשב, והמ"ע כותבת את התוכן של הפסיקה

- פסיקה - interrupt - סיגנל למ"ע להתיחס - שני סוגים של פסיקות:
- 1. פיסקת תוכנה - TRAP
- 2. פסירת חומרה - פשוט INTERRUPT

### Device status tabel:
- Device-status table contains entry for each I/O device indicating its type, address, and state.
- Operating system indexes into I/O device table to determine device status and to modify table entry to include interrupt.

### DMA - Direct Memory Access
- מנגנון אשר מונע את המצב שהמעבד מחכה יוצר נדי (שכל המידע יגיע בשלמות ואז יועבר לזיכרון)
- יתרונות המנגנון:
- פחות פסיקות 
- חיסכון בזמן מכיוון שהדרייבר לא מדבר ישירות עם הבקר אלה הבקר רושם ישר לזיכרון
- חיסרונות:
- עוד רכיב חומרה פיזי (אפשר להגיד עלות)

- מצגת 3 צריכה להכנס פה איפשהשנו
## - Week 3:
#### The Process Concept
- כל TASK או JOB נקראה תהליך PROCESS
- תהליך זה - זואי תוכנה שרצה
- לתהליך כזה יש זכרון אשר מחולק לשלושה חלקים:
    - טקסט\קוד סקשן - text\code section - המקע הכי חשוב אלה הם ההוראות של המעבד לתוכנית
    - דאטה סקשון - data section - משתנים גלבלים של התהליך
    - סטאק סקשן - stack section - משתנים מקומיים של התהליך
### יצירת תהליך:
- כל תהליך נוצר מתהליך אחר כלומר תהליך אב (תהליך הראשון נוצר ע"י מ"ע)
- קיים מושג עץ תהליכים
- תהליך אב לא יכול להשתחרר לפני שתהליכי בנאב ישוחרורו
- מבחינת חשיפה יש שלושה מקרים:
1. בן יכול לרשת את כל המשאבים של האב
2. בן יכול לרשת חלק מהמשאבים של האב
3. בן יכול לא לרשת משאבים כלל

### סיום של תהליך:
- תהליך מסתיים כאשר נגמר ה MAIN כלומר סיים את הקוד
- תהליך מסתיים כאשר בקוד מתבצאת קריאת לפונקצית מערכת EXIT()
    - בעזרת EXIT() ניתן לעביר מידע מהבן לאב
    - הפונקציה EXIT מקבלת פרמטר אחד - מספר(מספר זה מועבר לאב בסוף תהליך הבן)
    - האב מקבל את המספר באמצאות WAIT()
- כל תהליך יכול להרוג תהליך אחר ע"י KILL()
    -  פונקציה זאת נועדה לא לרק לאפסקת תהליך אלה גם להעברת מידע בין תהליכים
    - כאשר תהליך אב מת לפני בניו הבנים שלו משתיחים לפונקצית INIT 

#### Process states:
1. NEW - כאשר תהליך נוצר
2. RUNING - תהליך רץ
3. WAITING - תהליך השאיה מחכה ל event מסוים
4. READY - התהליך מוכן לרוץ
5. TERMINATED - תהליך סיים לרוץ
6. ZOMBIE - כאשר תהליך בן הסתיים אך האב לקיבל את ה RETURN VLAUE של התבליך הבן

- wating ו- ready - יכולים להיות מבלבלים:
- ready - כאשר התהליך מוכן לרוץ כלומר הוא לא עשוק 
- waiting - במהלך הקוד של התהליך יש איזהשהיא אשיה שלומר התהליך מחכה לעירוע מסויים

#### PCB:
### PCB - Process Control Block:
- לכל תהליך יש PCB משלו אשר שמור ומתוחזק ע"י מ"ע
- בתוך הPCB שמורים:
    1. מצב התהליך
    2. מספר סידור PID
    3. קאונתר - Counter - מספק אינדוקציה מה לעשות לאחר קריאת התהליך
    4. ה CPU Register - שומרת את הערכי האוגר
    5. ה CPU Scheduling Info - כמה זמן התהליך קיבל
    6. ה Memory menegment - גודל ואיזור הזיכרון המוקצע
    7. ה Accounting info - כמה זמן ריצה התהליך קיבל בכללי
    8. ה I\O info - באיזה קבצים השתמש התהליך


#### Scheduling
### תורי תזמון תהליכים:
- במ"ע תהליכים שמורים ברשימה מקושרת
- רשימה מקושרת אחת לכל תהליך
- רשימה מקושרת אחת לכל התקן חומרה - Device status tabel  
- וגם קיים שםIO device queue לרשימה של התקן חומרה
- וגם קיים שם ready queue לתהליכים שמוכנים לקוץ
- תהליכים נוגגים בין תורים אלו

קיימים שני סוגים של תהליכים:
1. I\O bound process - תהליך שזקוק להתקן חומרה ולכן נמצא הרבה במצב WAITING
2. CPU-Bound process - תהליך שזקוק לקריאות מעבד

קיימים עוד שני סוגים של תהליכים: 
1. Independent process - תהליך זה לא מושע או מפשיע על אחרים
2. Cooperating process - תהליך זה מושפע ומשפיע
### מתזמן:
- שני סוגי מתזמן:
    1. טווח ארוך - long-term scheduler
    2. טווח קצר - short-term scheduler

- מתזמן טווח קצר הרבה יותר מהיר וקובע כל כמה מילישניות איזה תהליך רץ
- מתמן טווח ארוך הרבה יותא איטי וקובע כל כמה שניות, לכן קוראים לו בתדירות נמוך יותר



#### Context Switches.
 - A context switch can occur as the result of an interrupt, such as when a task needs to access disk storage, freeing up CPU time for other proccess. 
 - Some operating systems also require a context switch to move between user mode and kernel mode procceses. 
 - החלפה לתהליך אחר ע"י CPU דורשת שמירת המצב הקיים של התהליך הישן והתחול התהליח החדש.
 - פעולה זאת נקראת context switch
 - תהליך רץ ב user mode ברגע פסיקה עובר ל kernel mode
 - מ"ע מעלה את ה PCB ומחזירה ל- user mode
 - פעולה זאת גורמת ל overhead ומ"ע לא עובדת בזמן זה
 - כמות הזמן שמ"ע לעובדת תלוי בחומרה

## - Week 4:
#### Process Communication:
### מנגנונים להעברת מידע בין תהליכים:
1. Producer - consumer - shared memory
   -  מ"ע מאפשרת לשני תהליכים לתקשר דרך יצירת תור
   -  To allow producer and consumer processes to run concurrently, we must have available a buffer of items that can be filled by the producer and emptied by the consumer.
   -  מ"ע מעבירה תהליכים ממצב running למצב waiting כדי לפנות מקום בתור
   -  הפתרון יכול למלא רק N-1 איברים
   -  בנוסף הוא מבצע busy waiting
2. תקשורת ישרה - תקשורת בין שני תהליכים באמצעות הודעות
3. תקשורת שאינה ישירה - תקשרות באמצאות משאב אחר לדוגמע PIPE, תומך בתקשורת בין הרבה תהליכים
4. סינכרוניזציה - blocking and non-blocking
- blocking is like tcp awating for the whole messege to pass before passing on 
- non-blocking is like udp just sends messeges and could care less about whats up with them ;)

### שיטת העברת הודעות באמצעות buffering:
עובדת עם תור של הודעות
1. מקסימום 0 הודעות כלומר אין buffer ששומר הודעותף, השולח מכחה שהמקבל יקרא ב שיטת ה blocking וזאת שיטת ה - Zero capacity
2. מקסימום n הודעות בתור, כשאר התור מלא השולח מחקה שהתור התרוקן - Bounded capacity
3. התור אינסופי, לא נדרש לחקות - Unbounded capacity 



## - Week 5:
#### CPU bursts, I/O Burst Phases:
אורך חיים של תהליך יש לו:
- חתיכה של CPU BURST
- חתיכה של I\O BURST

- מתזמן רץ ומתרתו לנצל CPU בצורה מקסימלית
CPU - I\O - burst cycle:
 - ריצה ב CPU המתנה ל-I\O, תהליך עובר בין שני המצבים אבל נגמר ומתחיל רק ב- CPU
 
CPU scheduler - מתזמן המעבד:
- בוחר תהליך ה ready queue וסם אותם במעבד
הוא בוחר כשאר:
1. תהליך עובר ממצב runing למצב waiting (למשל בפעולת קלט\פלט)
2. תהליך עובר ממצב runing למצב ready (קורה במצב של פסיקה מה timer)
3. תהליך עובר ממצב waiting למצב ready (כאשר פעולת IO הסתיימה)
4. תהליך עובר ממצב runing למצב terminated (כלומר סיים לרוץ)

- עם המתזמן מעביר יכול להעביר תהליך בכל מ 4 האפשרויות אז הוא נקרה - prempative
- עם המתזמן לא מעביר את התהליך למצב ready אז הוא נקרה - non-prempative

במילים פשוטו:
preemptive - 
- מ"ע יכולה לעצור תהליך האמצע, והוא יכול להמשיךלרוץ לבד 
non-preemptive - 
- מ"ע מריצה תהליך רק עם התהליך תקוע

רוב המחשבים היום הם עם preemptive - רוב הסיכויים שגם זאת תהיה תשובה במבחן עם שואלים על אורך חיים של תהליך


Dispecher module -  
he is part of the scheduler and he does:
1. Context switch
2. Swuitches to User mode
3. Jumps to the correct place in the code


#### Scheduling Criteria
קרטריונים בם משתמשים להשווה של מתזמנים:
1. זה CPU utilization - ניצול ה- CPU
2. תפוקה - throughput 
3. זמן סבב - turnaround time - כמה זמן לוקח להריץ תהליך
4. זמן המתנה waiting time - כמה זמן עובר עד שתהליך במצב ready 
5. זמן תגובה response time 



#### Scheduling Algorithms.

1. FCFS - First Come First Served - FIFO
2. SJF - Shortest Job First
3. Priority Scheduling -
- לכל תהליך מוקצע עדיפות INT, ככל שהמספר נמוח חותר עדיפות גבוהה יותר. עם לשני תהליכים יש עדיפות שווה אז הבחירה תתבצע לפי FCFS, אחת הבעיות שיכולות לקרות זה STARVASION שתהליך פשוט לא מקבל זמן CPU
- הפתרון ל בעיית ההרעבה - AGING - שיטה כדי להגדיל את העדיפות של תהליך ככל שזמן המתנה גדל
4. RR - Round Robin - 
- בשיטה זאת קיים פרמטר QUANTUM - הוא אחריי להגדיר זמן עבור כל תהליך. תור ה READY - FIFO, ותהליך חדש מתבסף לסוף התור
5. Multilevel Queue - 
- בשיטה זאת מחלקים את תור התהליכים לכמה תורים שונים וכל תור יכול לעבוד בשיטה שונה (RR, FCFS, SJF, Priority)
7. Multilevel Feedback Queue - 
- כמו שיטת ה multilevel רק שתהליך גם יכול לעבור בין התורים 

## - Week 6:

#### Race Condition:
סינכרון בין תהליכים:
1. נניח וישלנו ערך 1000 ששמור בכתובת address1 ב RAM
2. נריץ שני אלגוריתמים שרושמים לאותה הכתובת, Proccess A and Proccess B
3. עם נריץ תהליך A ואז B אז הערך הסופוי = 800
4. עם נריץ תהליך B ואז A אז הערך הסופי = 900 בגלל הקוד שכתוב
5. זה נקראב race condition שהתוצאה תלוי בסדר ההוראות
6. אנו נרצה שהתוצאה תמיד תהיה שווה לא משנה סדר התזמונים.

ה RACE CONDITION - זה מצב בא שני תהליכים מנסים לגשת או לשנות בו זמנית משאב משותף, כדי למנוע מצב כזה על התהליכים להיות מסונכרנים.


#### Critical Sections
- קטע קריטי זה קטע קוד בתוכנה, 
- התוכנה מורצת על ידי כמה תהליכים, וכמה תהליכים צריצים את אותו קטע קוד,
- אני צריכים ש:
- שני תהליכים בחיים לא היו באותו קטע קוד קריטי ביחד בו זמנית
- תהליך שמגיע לקטע קוד קריטי יעלץ לחקות לתהליך שבפנים שאסיים (במידה ותפוס)
- פתרון בעית הקאע הקוד הקריטי זה אוספת קוד בכניסה ויציאה מהקטע, שעושים מעקב לכל תהליך שנכנס ויוצא

3 תנאים לפתרון העיה:
1. Mutual exclusion - מניעה הדדית, עם יש תהליך בקטע הקריטי אף תהליך לא יכול להכנס לשם גם בכוח
2. Progress - עם אין שום תהליך בקטע הראשון שמגיע ישר נכנס
3. Bounded waiting - הרבה תהליכים מחכים חייבים להיות עם פרק זמן המתנה סופי כדי למנוע הרעבה

#### Algorithms.
#### אלגוריתם ראשון - אלגוריתם נאיבי
- שימוש במשתנה TURN ששווה 0 או 1
- לפי ערך ה TURN אנו נותנים לתהליך אפשרות להכנס
- עם זה לא תור התהליך אז הוא מחכה בלולאה אין סופית
- בסוף הקטכ הקריטי התהליך משנה את ערך ה TURN

#### אלגוריתם שני - אלגוריתם משופר
- מאתחלים מערך בוליאני => flag[0] = flag[1] = false
- עם תהליך נכנס לקטע הקריטי flag[i] = t
- עם תהליך j נוסף מגיע לקטע אז מחכה לתורו 
- כשאר תהליך בקטע מסיים את ריצתו משנה גם את ערכו ל flag[i] = false
- ותהליך j יוצא מהלולאה ונכנס לקטע הקריטי
- באלגוריתם זה יש את בעית ה bounded waiting
- וסכנה ל deadlock משום שכל התהליכים יכולים להצליח להכנס לקטע קוד הקריטי

#### אלגוריתם שלישי - אלגוריתם מתקדם
- אלגוריתם זה שילוב של השניים
- אלגוריתם 1 ו אלגוריתם 2 לא אלגוריתמים טובים אך השילוב שלהם יוצר אלגוריתם טוב
- אלגוריתם שמשלב את השניים הקודמים פטרון הבעיה קטע קיריטי רק עבוד שני תהליכים

### BAKARY ALGORYTHM - אלגוריתם המעפיה
#### פותר את בעית קטע קוד קריטי עבור מספר תהליכים
1. לפני כניסה לקטע התהליך מקבל מספר - ticket
2. המספר זה כמו תור והוא קובע מי נכנס הבאה (מהקטן לגדול - כמו בדואר)
3. יכול להיות ששני תהליכים יקבלו אותו מספר, במצב הזה בוחרים את התהליך עם ה PID הקטן יותר שיכנס ראשון (כי המ"ע פשוט תראה אותו לפני)
4. סדר המספרים זאת סידרה עולה (לא מדויק)
5. באלגוריתם מבצעים שימוש בשני מערכים משותף וזהו ה shared memory של התהליכים
6. מערך ה PID - עכרי על סדר
7. מערך ה CHOOSING - עכרי על זה ששני תהליכים לא יכנסו לקטע הריטי ועל mutual exclusion

 
## - Week :

####  Hardware based Scheduling
- test and set - tests the proccess and the sets the value it returns
- swap - swaps the value of the process with the value stored in the memory 

#### Semaphores
- זאת היא תוכנה של המ"ע שמאפשר למ"ע לטפל בבעית הקטע הקריטי
- המ"ע מבצאת שימוש ב test and set ו- ב swap

#### שני סוגים של סמפורים:
1. ה counting semaphore - הערך שלו יכול להיות כל מספר שלם
2. ה binary semaphore - אפסים ואחדים (קל למימוש ויותר יעיל) 




#### Classic Scheduling Problems:
## שמות הבעיות התזמון הקלאסיות:
1. בעיית ה Bounded-Buffer - יצרן צרחן
2. בעיית ה Readers-Writers - קוראים כותבים
3. בעיית ה Dining-Philosophers - הפילוסופרים הסועדים


### Bounded Buffer Problem:
- בעיית היצרן צרכן - פותר semaphore.
- ישנם 3 semaphores 
- 2 תהליכים - יצרן Producer ו- צרכן Consumer
- The producer stores data in the buffer(array) 
- The consumer removes data from the buffer
- The produce and consumer should not insert and remove data simultaneously

- Three semaphores:
1. mutex - binary semaphore 
2. empty - a counting semaphore - initual value is the number of slots in the buffer, since all slots are initially empty
3. full - a counting semaphore - initual value is 0




#### Deadlocks.

## - Week :
#### Addressing
#### Memory Allocation
#### Fragmentation.

## - Week :
####  Paging
#### Segmentation
#### Virtual Memory
#### Page Faults
#### Page replacement Algorithms
#### Thrashing.

## - Week :
#### File Structure,
#### File Systems
#### Directories
#### File Allocation.

## - Week :
####  Vacant Space Management
#### Log Files
#### File Recovering
#### Distributed File Systems.

## System calls (relevant):
 - execl – טוענת קוד חדש לתוכנית.
 - execv – מבצע קטע קוד אחר. אם הפקודה מצליחה אז היא לא ממשיכה לקוד שאחריה.
 - wait – קריאת מערכת שגורמת לתהליך להפסיק לקבל זמן מעבד עד שאחד הילדים שלו מת.
 - fork – יצירת תהליך חדש.
 - semop – מבצע פעולות על סמפורים נבחרים בסט המצוין ע"י semid. (אפשר לעשות איתו פקודות אטומיות).
 - semctl – פונקציית בקרה על הסמפורים.
 - semget – קריאת מערכת שפונה ל- kernel, יוצרת semaphore set ומחזירה את המזהה שלו.
 - shmget – אומרת למערכת ההפעלה להקצות אוסף זיכרון אצלה בתוך ה- kernel. הפונקציה מחזירה מזהה.
 - shmdt – Shared memory detach- ניתוק (שחרור) אוסף הזיכרון מ- page table.
 - shmat – shared memory attach – חיבור אוסף הזיכרון ל- Page table. מחזיר את הכתובת הלוגית שממנה ניתן לגשת לזיכרון המשותף.
 - shmctl – shared memory control- נשתמש בה כדי למחוק את הקצאת הזיכרון על מנת למנוע זליגת זיכרון.
 - exit – פונקציה אשר הורגת תהליך  הופך ל- terminated) ומחזירה מספר.
 - printf – מבצע I/O למסך ולכן הוא חייבת לעבור דרך מערכת ההפעלה.
 - scanf – מבצע I/O ולכן חייב לעבור דרך מערכת ההפעלה.
 - ipcrm – מוחק אובייקט מרחף בזיכרון.
 - ipcs – מראה איזה אובייקטים מרחפים בזיכרון.
 - nice – מאפשרת לשנות עדיפות של תהליך בלינוקס. היא מורידה או מעלה עדיפות (פקודה יזומה).
 - Mount, Unmount- מחברת תת עץ למערך.
 - ps (process status) – מראה רשימה של התהליכים במערכת ובאיזה מצב הם. Ps עובד עם דגלים.
 - df- Disk Free.
 - Top – כמו ps.
___________
- 2^10 = 1KB
- 2^20 = 1MB
- 2^30 = 1GB
- 2^40 = 1TB
- 2^50 = 1PB
- 2^60 = 1EB



## Contributing

Feel free to contribute to this repository by adding additional study materials, practice questions, or improving the existing content. Just create a pull request, and I'll review the changes.

## License

This project is licensed under the [MIT License](LICENSE).


