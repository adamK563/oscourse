# Operating Systems Exam Preparation

This repository contains my preparation materials for the "Operating Systems" exam. The exam covers various topics related to operating systems, including process management, memory management, file systems, and synchronization.

## Study Plan
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
4. מקום בדיסק בשם Spool, הספול שומר תהליכים איטים לרכיבי חומרה איטים spooling


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
####  Storage
#### Interrupts

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

## Contributing

Feel free to contribute to this repository by adding additional study materials, practice questions, or improving the existing content. Just create a pull request, and I'll review the changes.

## License

This project is licensed under the [MIT License](LICENSE).


