Сначала я экспортировала файл words@... как текст с разделителями. После, используя регулярные выражения, оттуда достала сами слова.

поиск: ^(.*)\t

заменить:(ничего)

Остались только нужные слова, копирую этот столбец и вставляю в Mystem. После этого копирую получившийся морфологический анализ в очередной текстовый файл и с помощью тех же регулярных выражений достаю леммы и морфологические свойства.


лемма:

поиск: 

  ```^(.*)\{(.*?)\=(.*)\}```

заменить: \2

морфология:

поиск: 

  ```^(.*)\{(.*?)\=(.*)\}```

заменить: \3

Из самого первого импортированного файла @words... копирую 2 столбика: время начала и время окончания, вставляю в excel. В 3ий столбик сначала вставляю леммы, копирую все три столбца в отдельный текстовый файл lemma.txt, то же самое делаю со столбиком морфологии и вставляю все в файл morph.txt.
Импортирую файлы lemma и morph в elan, 1 столбик - время начала, 2 столбик - время окончания, 3 столбик - аннотация.


Mystem довольно хорошо справился с определением леммы всех слов, за исключением "эмм". В этом слове он не распознал междометие и привел лемму имени "Эмма", поэтому определяет ее как "S". Ему впринципе не поддавались междометия "эм", на них он выдавал "ээ{ээ??}".
То же самое происходило и с "иии", он выдавал "иии?".
Что касается морфологии, Mystem справился со всем, кроме "ну". У "ну" есть два значения в качестве частицы и междометия в заивисмости от контекста. Mystem всегда определял "ну" как частицу. Также, у  Mystem, видимо, нет функции определения пунктуации, потому что он не дает никаких комментариев к знакам препинания. Отмечу, что он правильно обозначил "сборная"(спортивная) как "S", а не "ADJ". Только сразу после этого предлог "в" обозначает за аббревиатуру, возможно, это связано с тем, что после него стоит слово с большой буквы. То же самое происходит с "в", "к " и "с" и в других ситуациях "в художественной школе...", "к нему...", "с днем...". Не обозначает "надо" как предикат, а как "ADV". Mystem очень любит предлоги и союзы определять за существительные, это систематически происходит и с предлогом "с". "Это" определяет за SPRO, по корпусу это возможно, по словарю Зализняка "это" является частицей. "А" союз определяет за частицу в контексте противопосталения "...а он ну". Также проблемы с определением морфем у "типа" и "там".

Mystem отлично справляется с определением морфем, кроме каких-то редких случаев с междометиями. Испытает сложности с определением морфем многих предлогов и реже союзов. Отлично справляется с определением морфем существительных, глаголов, прилагательных и других. Если исправлить повторяющие системные ошибки, то Mystem будет выполнять работу с практически 100% качеством.
