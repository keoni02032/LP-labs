# Реферат
## по курсу "Логическое программирование"

### студент: Семенов И.М.

## Типовые и бестиповые логические языки: обзор и сравнение.

### Понятие типа и типизации

Понятие типизации появилось в первую очередь в связи с появлением понятия переменной в языках программирования. Как мы помним, переменная - некоторый непрерывный промежуток памяти, выделенный программе для использования и имеющий уникальное имя(такое определение подходит для императивных языков программирования). Так как работать с "сырым" куском памяти не очень удобно, во многих языках для переменных был определен набор типов, которые могут характеризовать переменные. В частности тип задает множество значений, которые переменная может принимать, правило интерпретации значений этого типа(последовательности битов, хранящейся в памяти), операция и отношения, определенные над значениями типа. Присвоение переменной типа также позволяет определить, сколько именно места в памяти она должна занимать. Под типизацией же можно понимать принцип, характеризующий назначение каждой переменной определенного типа.

Тип переменной должен зафиксироваться до того, как с ней будут произведены какие-либо операции. Типизация также позволяет сделать синтаксис более строгим и не позволять проводить недопустимые операции. Это, в свою очередь, помогает более эффективно обнаруживать различные несоответствия и ошибки(зачастую еще на этапе компиляции).

В языках логического программирования под переменной подразумевается совсем другая сущность, нежели в императивных языках. Здесь все переменные являются просто ссылками, указывающими на некоторую произвольную структуру. Операция явного присваивания значения тоже отсутствует. За заполнение переменных некоторыми значениями отвечает механизм, называемый унификацией. Унификация позволяет сопоставлять значения переменным в процессе вызова предикатов, что в комбинации с бэктрекингом дает широчайшие возможности для перебора вариантов, а это является одним из основных преимуществ логических языков.

Кажется, что необходимость типизации в логических языках отсутствует? Все переменные являются лишь ссылками, а программисту не нужно думать о том, сколько та или иная переменная будет занимать в памяти(так как в декларативных языках программирования процесс написания программы отделен от процесса вычислений, совершаемых ей). На самом деле, как уже было упомянуто ранее, благодаря типизации можно избежать большого количества ошибок. При написании программ на бестиповых языках логического программирования, постоянно приходится держать в памяти сигнатуры используемых предикатов. При написании большой и сложной программы это становится довольно утомительным. Программа на Прологе, к примеру, завершится неуспехом, если такая ошибка будет иметь место. Для исправления придется прибегнуть к долгой и неприятной отладке, хотя при наличии типовой системы проблема могла бы быть обнаружена сразу же. 

Итак, такая ошибка может возникнуть в любом месте программы, но если язык нетипизирован, то интерпретатор/компилятор никоим образом не сможет помочь в ее обнаружении. Пролог является здесь отличным примером, так как он является бестиповым интерпретируемым языком. Любая переменная в нем может иметь совершенно произвольное содержимое. Я на личном опыте смог убедиться, как такая архитектура языка усложняет отладку. Для устранения этого недостатка могут использоваться надстройки над языками, а также типизированные логические языки программирования. 

Типизация позволяет значительно упростить поиск ошибок. Также, благодаря типизации можно создавать более производительный и понятный код, так как принимая некоторые аргументы в предикат, во многих случаях приходится проверять их содержимое. Такие проверки могут стать ненужными при появлении в языке типизации.

Существует несколько категорий ошибок, которые могут появиться в логических программах. В частности к ним относятся ошибки, связанные с неправильным взаимодействием предикатов друг с другом. Причиной таких ошибок может стать неправильное упорядочивание аргументов, несоответствие реального содержимого переданного аргумента с ожидаемым и прочие ошибки, которые вызваны в основном тем, что язык предоставляет только один тип данных - универсальный. 

Проверка типов в языках логического программирования полезна по многим причинам. Она позволяет писать гораздо более читабельные и простые для понимания программы. Также, декларирование и проверка типов обеспечивают уверенность в том, что код программы написан правильно и она будет работать именно так, как задумывалось.

### Виды типизации и классификация языков

Классификация языков по их типизациям опирается на несколько параметров, в первую очередь на то, насколько существенны ограничения, налагаемые синтаксисом на программиста.

В зависимости от серьезности этих ограничений, разделяют следующие типы языков:
1. Языки со строгой типизацией(Java, C#, Mercury, SML и.т.д), в которых соответствие типов выражений соблюдается последовательно и строго.
2. Языки с нестрогой типизацией(C, C++), в которых тип данных используется главным образом для определения размера выделяемой под переменную области памяти
3. Бестиповые языки(Prolog, LISP), в которых переменные могут принимать произвольные значения различной природы по ходу выполнения программы. Иными словами можно считать, что эти языки имеют один универсальный тип данных, покрывающий все возможны в рамках языка объекты.

Безусловно, уровень типизации языка не может быть определен строго и причислен к одной из упомянутых групп. Приведенное разделение является достаточно условным. Уровень типизации языка - субъективная величина, варьирующаяся в зависимости от различных факторов, присутствующих в языке.

Языки логического и функционального программирования изначально были бестиповыми, чтобы следовать структуре базовой математической теории(логики предикатов и лямбда-исчисления соответственно). Кроме того, системы ИИ, для реализации которых по большей части и создавались первые логические и функциональные языки, были призваны оперировать слабоструктурированными и сильносвязными данными, для которых попытки типизации могли привести к уменьшению выразительности или возрастанию сложности моделей.

В разработке ПО наблюдаются следующие закономерности:
1. Использование языков с сильной типизацией замедляет изначальный процесс разработки программного обеспечения, но существенно сокращает отладку, так как множество ошибок, вызванных несоответствием типов проявляют себя еще на этапе компиляции.
2. Бестиповые языки или языки со слабой типизацией более удобны для быстрого создания работоспособных прототипов, но полученные программы требуют более тщательной отладки и содержат больше ошибок.

Таким образом, внесение типизации в неимперативные парадигмы программирования позволяет приблизить соответствующие языки к стандартам систем промышленной разработки. Однако, внедрение понятия типа в такой вычислительный формализм, как логика предикатов, требует определенного математического уточнения понятия типа данных.

### Статический и динамический контроль типов

Различают 2 вида контроля типизации в языках программирования:

 1. Статический, типы переменных проверяются по тексту программы до ее выполнения программы, на этапе компиляции. Большим преимуществом такой типизации является тот факт, что большую часть ошибок типов можно найти на ранней стадии разработки. Статическая типизация обычно приводит к более быстрому исполнению скомпилированного кода, потому что компилятор знает точные типы используемых данных и создаёт оптимизированный машинный код. Статическая проверка типов оценивает лишь информацию, доступную во время компиляции, а также может подтвердить, что проверенные условия соблюдаются для всех возможных вариантов исполнения программы, что избавляет от необходимости проверки перед каждым запуском программы. Без статической проверки типов даже 100%-ное покрытие тестами не всегда поможет выявить некоторые ошибки типизации.
 2. Динамический, осуществляемый в процессе выполнения программы. В отличие от статической проверки типов, динамическая может привести к прекращению выполнения программы из-за ошибок типизации. В некоторых языках этого может избежать (например, благодаря обработке ошибок или слабой типобезопасности). Для избежания подобных ситуаций рекомендуется использовать юнит-тесты. Код, прошедший динамическую проверку типов, в общем случае менее оптимизирован; кроме того, существует возможность ошибок выполнения и, как следствие, необходимость проверки перед каждым запуском. Тем не менее, динамическая типизация открывает дорогу другим, мощным техникам программирования, например, метапрограммированию. Стоит отметить, что часто можно добавить в бестиповые языки динамический контроль типов с помощью тех или иных надстроек(возможно, созданных вручную).

Вообще говоря, можно считать, что динамическим контролем обладают все системы программирования, так как при попытке запуска программы, содержащей запрещенные операции зачастую возникнет ошибка выполнения.

Логика предикатов первого порядка и соответствующие системы логического программирования содержат встроенные возможности по динамическому контролю типов в виде структурных термов. Предикаты не применяются к значениям, имеющим неподходящую структуру – т.е. с учетом обозначений к значениям другого типа. В случае с Прологом можно оборачивать определенные значения в соответствующие структурные термы. Если перепутаем параметры, передаваемые в предикат, – несоответствие типов приведет к тому, что аргументы будут унифицироваться не так как нужно, что приведет к отказу. Это лучше, чем если бы такого контроля вообще не было. Но, на самом деле, все не так хорошо, как кажется на первый взгляд. Ошибкой это все-таки не будет, будет просто неуспех. Если хотим, чтобы выдавалась ошибка типизации, нужно описать еще одно правило, если в случае того, что что-то не то было передано, выдавалось сообщение об этом. 

Однако интерес представляет именно статический контроль типов, который позволяет обнаруживать ошибки в программах до их выполнения, т.е. по сути дела на этапе разработки, а не тестирования. Для этого необходимо произвести расширение логики предикатов понятием системы типов – т.е. формальной аксиоматической системы со своими аксиомами и правилами вывода, целью которой будет проверка соответствия типов в выражениях логики предикатов.

### Системы типов. Многосортная логика предикатов. Корректность системы типов

Типом в логическом языке программирования является набор некоторых структурных термов. В этих термах позиция аргумента связана с тем, какого наполнения ожидает программист от этого терма. Типы вводятся в языки логического программирования с целью получения возможности отличать значимое от не имеющего смысл. Соответственно, в программах на Прологе не нужно как-либо декларировать типы, так как типы объектов распознаются по их синтаксической форме в тексте программы(например, атомы начинаются с маленькой буквы или заключаются в одинарные кавычки, строки заключаются в двойные кавычки).

Для создания механизма статического контроля типов в логическом языке, необходимо в первую определить формальную теорию исчисления типов. Система типов в общем случае строится параллельно с операциями базовой формальной логики. Общая его идея состоит в том, что вводится множество типов, и понятия объявления типа и окружения. Также определяется понятие выводимости объявления, означающее, что в некотором окружении можно сделать вывод о типе терма. Также определяются правила, согласно которым делаются заключения о выводимости того или иного типа. Классическая логика предикатов, расширенная системой типов называется многосортной логикой предикатов. Обычно для реализации многосортной логики предикатов используется система Майкрофта О'Кифа. 

Корректность системы типов - свойство формальной системы вывода типов, которое формулируется следующим образом: если выражение типизированно корректно и из него с помощью правил вывода можно получить другое выражения, то оно тоже корректно типизированное. Коротко говоря, это свойство сохранения правильности типов при выводе. Из корректности системы типов следует, что типизация будет корректной на всем протяжении выполнении программы, если она была корректна до компиляции.

### Режимы доказательства. Детерминизм

Режимы вызова предикатов и детерминизм относятся к процедурным особенностям использования предикатов.

Одной из основных особенностей предикатов в парадигме логического программирования является то, что почти любой предикат можно использовать несколькими способами, в зависимости от передаваемых в предикат аргументов и степени их унифицированности. Такая особенность называется режимом вызова или режимом доказательства предиката. При этом для различных режимов строятся совершенно разные деревья SLD-резолюции. Это может быть учтено и использовано системой программирования, например, Mercury создает и оптимизирует код для каждого отдельного режима.

Как уже было сказано, режим вызова определяется унифицированностью переданных переменных. Говоря конкретнее, необходимо определить выходные и входные переменные предиката. Входной называется переменная, унифицированная на момент вызова предиката, выходная же на момент вызова должна быть неунифицированной, она унифицируется только к моменту завершения работы предиката. Однако, не всегда можно точно определить, унифицирована ли переменная, или нет. В таком случае нужно ввести понятие, называемое классом конкретизации. Оно определяет степень унифицированности переменной.

Стоит отметить также такую характеристику предиката, как детерминизм. Эта характеристика позволяет понять, какого результата ждать от предиката. Для определения детерминизма конкретного предиката необходимо знать, сколько будет решений и возможен ли отказ.
1. 0 решений, отказ невозможен - некорректный случай.
2. 0 решений, отказ возможен - выполнение предиката всегда будет порождать неуспех.
3. 1 решение, отказ невозможен - функция в классическом пониманий, такой предикат называется детерминированным.
4. 1 решение, отказ возможен - полудетерминированная функция. Ведет себя почти как функция, но порождает отказ на некотором диапазоне аргументов.
5. Несколько решений, отказ невозможен - мультидетерминированный предикат.
6. Несколько решений, отказ возможен - недетерминированный предикат.

### Типы в Prolog

Prolog - бестиповый язык, следовательно он имеет один универсальный тип данных(терм), к которому и относятся все возможные сущности, определенные в языке. Термы делятся на простые и структурные. Простые термы включают в себя константы и переменные. Константы, в свою очередь, могут быть представлены числами или атомами.

Более подробное описание возможных типов:
1. Атом - константа, соответствующая объекту предметной области, которую описывает программа. 
2. Числа - почти не отличаются от атомов по своей сути, но для них определены структурные термы, представляющие арифметические операции, а также оператор is, позволяющий инициировать числовые вычисления.
3. Переменные - записываются в виде идентификаторов, начинающихся с заглавной буквы. Являются заполнителями для произвольных термов.
4. Составной терм - атом, состоящий из названия(функтора) и списка аргументов. Такие термы удобны для представления сложных структур данных.
5. Список - не является термом, но имеет не меньшее значение. Определяется рекурсивно, как некоторый головный элемент, и хвост(также являющийся списком). Может быть представлен в виде совокупности структурных термов .(H, T) . Пустой список обозначается как [].
6. Строки - последовательность символов, заключенных в кавычки. Является по своей сути списком ASCII кодов этих символов.

Prolog предоставляет динамический контроль типов.

### Mercury

Mercury - современный язык функционального программирования. Заимствует часть синтаксиса у Prolog, но предоставляет множество значительных улучшений.

Mercury является строго типизированным, предоставляет средства для модульного программирования и объектной ориентированности.

Программа на языке Mercury включает в себя следующие элементы:
* :−module – заголовок модуля.
* :−interface – интерфейсная часть, здесь описано то, что должно быть доступно другим модулям. Чтобы программа была исполняемой, хотя бы один модуль должен экспортировать управляющий предикат main(который должен выполнятся без возвратов).
* :−import_module – импорт из других модулей.
* :-type – пользовательские типы данных.
* :−pred – определение предиката, в нем указываются типы аргументов, его режимы варианты детерминизма.
* Каждая программа в Mercury должна иметь определение предиката main, с которого начинает работу программа.
* :−implementation – реализационная часть модуля, содержит реализации всех необходимых предикатов.

Благодаря строгой типизации, можно с определенной долей уверенности говорить о том, что если программа на Mercury запустилась, то она работает корректно.

### Вывод
Типизация в языках программирования позволяет уменьшить время, требуемое на отладку программ за счет увеличения времени на написание программы. С помощью статического анализа компилятор может точно указывать на ошибки в использовании типов. 

Преимуществом бестиповых логических языков является простота и скорость написания программ. Отсутствует необходимость описания типов и режимов предикатов. Но это порождает и серьезные минусы, которые заключаются в том, что поиск ошибки в программе может занять довольно много времени. К минусам Пролога в частности также относятся его низкая скорость и необходимость задумываться о структуре дерева резолюции, иначе можно получить неприятные результаты.

С другой стороны, типизированные языки логического программирования лишены многих недостатков классического Prolog. Благодаря строгой типизации возможно писать более надежные и быстрые программы. Такие языки больше подходят для разработки серьезного программного обеспечения, Prolog же довольно неплох в сфере обучения основам логического программирования, но не более.

### Литература

 1. Types in Logic Programming. Frank Pfenning. (1992)
 2. Парадигма логического программирования. Сошников Д.В. (2006)
 3. Prolog programming for artificial intilligence. Ivan Bratko (1990)

