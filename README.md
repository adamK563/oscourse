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
מערכת מבוזרת - Distrebuted system - מערכת של כמה מחשבים 
שיתוף משאבים
תפוקה
אמינות - עם מחשב אחד נופל המערכת ממשיכה לפעול

- Real-time systems
 ### סוגים של מערכות זמן אמת:
 1. Hard real-time systems: 
 A hard real-time system has absolute deadlines, and if those allotted time spans are missed, a system failure will occur.
 example: Iron Dome (97%+ success rate)
 
 2. Soft real-time systems, the system continues to function even if missing a deadline, but with undesirable lower quality of output.
 example: Smart fridge (We say thank if somehting smart happens)

## - Week 2:
####  Storage:

### סוגי זכרון במחשב:
1. זקרון מהיר - RAM - זכרון נמחק לאחר RESET
2. שטח דיסק - זיכרון משני - דיסק קשיח - HD - Hard disk
3. קאש - cache - זכרון זמני - נועד לשמור נתונים של ה CPU ותוכנות או תהליכים
4. אגרי מעבד - hardware register - תוכנות מחשב כותבות ומשתמשות בזכרון הזה כדי לתקשר עם המעבד

### HD מגנטי
צלחות מגנטיות - מסתובבות על ציר (קומות שונות) במקביל
משטח מגנות - צד אחד בצלחת מגנות (מלמלע ויש גם למטה)
ראש קורא כותב - ידית שקוראת 
סקטור - יחידה שנתן לקרוא
טראק - אוסף של סקטורים ברדיואוס של המשטח מגנות
צלינדר - אוסף כל הטראקס (מכל הצלחות) שבאותו הרדיאוס


#### Interrupts:

## הקדמה:
חיבור פיזי שכל התקני חומרה מחוברים אליו - BUS 
לכל התקן חומרה יש בקר משלו (controller)
הבקר (controller) - מקשר בין הרכיב חומרה למעבד
קיימים שני התקני חומרה: מהיר ואיטי
התקן חומרה איטי: מדפסת
התקן חומרה מהיר: מסך, מקלדת, עכבר

### בקר Controller

המעבד לא מדבר בצורה ישירה עם התקן חומרה
המעבד מדבר עם הבקר כדי לקבל נתונים על הרכיב חומרה
למעבד יש Driver לכל בקר כזה בשביל תקשורת
לכל בקר יש buffer (זכרון קטן)

נקודות חשובות:
- התקני קלט פלט והמעבד עובדים במקביל
- לכל התקן חומרה יש בקר משלו
- לכל בקר יש buffer פנימי
- בקר מעדכן את המעבד על שינוי באמצאות פסיקה

### פסיקה:
לאחר קבל פסיקה המעבד מריץ (Interrupt service routine) ISR

שה ISR זה פונקציה לטיפול פסיקות.
פיסקה בנוי מ8 ביטים וגם כך המעבד יודע לזעות מאיזה סוג הפיסקה (לפי ה8 ביטים)

ה Interupt Vector - מכיל את כל הפסאות האפשריות שיש למערכת הפעלה בסדר לפי 8 הביטים
הוקטור שמור בRAM המחשב, והמ"ע כותבת את התוכן של הפסיקה

פסיקה - interrupt - סיגנל למ"ע להתיחס - שני סוגים של פסיקות:
- 1. פיסקת תוכנה - TRAP
- 2. פסירת חומרה - פשוט INTERRUPT

### Device status tabel:
Device-status table contains entry for each I/O device indicating its type, address, and state.
Operating system indexes into I/O device table to determine device status and to modify table entry to include interrupt.

### DMA - Direct Memory Access
מנגנון אשר מונע את המצב שהמעבד מחכה יוצר נדי (שכל המידע יגיע בשלמות ואז יועבר לזיכרון)
יתרונות המנגנון:
- פחות פסיקות 
- חיסכון בזמן מכיוון שהדרייבר לא מדבר ישירות עם הבקר אלה הבקר רושם ישר לזיכרון
חיסרונות:
- עוד רכיב חומרה פיזי (אפשר להגיד עלות)

## - Week 3:
#### The Process Concept, Process states, 
#### PCB,
#### Scheduling
#### Context Switches.

## - Week 4:
#### Process Communication, Threads.

## - Week 5:
#### CPU bursts, I/O Burst Phases 
#### Scheduling Criteria
#### Scheduling Algorithms.

## - Week 6:
#### Priority,
#### Multi-Level Scheduling
#### Distributed System Scheduling.

## - Week 7:
####  Critical Sections
#### Dijstra Algorithms and the Bakery Algorithm.

## - Week 8:
####  Hardware based Scheduling
#### Semaphores
#### Classic Scheduling Problems
#### Deadlocks.

## - Week 9:
#### Addressing
#### Memory Allocation
#### Fragmentation.

## - Week 10:
####  Paging
#### Segmentation
#### Virtual Memory
#### Page Faults
#### Page replacement Algorithms
#### Thrashing.

## - Week 11:
#### File Structure,
#### File Systems
#### Directories
#### File Allocation.

## - Week 12:
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

## Contributing

Feel free to contribute to this repository by adding additional study materials, practice questions, or improving the existing content. Just create a pull request, and I'll review the changes.

## License

This project is licensed under the [MIT License](LICENSE).


