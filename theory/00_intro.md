# Тема 00: Вводная

- [Тема 00: Вводная](#тема-00-вводная)
  - [Краткое содержание](#краткое-содержание)
  - [Актуальность верификации цифровых устройств](#актуальность-верификации-цифровых-устройств)
  - [Верификация процессорных ядер](#верификация-процессорных-ядер)
  - [Архитектура набора команд RISC-V](#архитектура-набора-команд-risc-v)
  - [Особенности RISC-V](#особенности-risc-v)
    - [Открытость](#открытость)
    - [Модульность](#модульность)
  - [Вектор развития RISC-V](#вектор-развития-risc-v)
  - [To be continued...](#to-be-continued)


## Краткое содержание

Данное занятие является вводным и рассказывает об актуальности верификации[^1] цифровых устройств и особой актуальности верификации процессорных ядер в настоящее время.

Также в ходе занятия дается краткое описание архитектуры набора команд RISC-V и ее особенностей, позволивших ей набрать популярность в последние годы. Описывается предполагаемый автором вектор развития RISC-V.


## Актуальность верификации цифровых устройств

Индустрия микроэлектроники последние несколько десятков лет развивается действительно впечатляющими темпами. [Закон Мура](https://en.wikipedia.org/wiki/Moore%27s_law) продолжает выполняться по сей день, "удваивая" количество транзисторов в цифровых устройствах каждые 2 года. Очевидными тенденциями являются увеличение количества функциональных блоков, возрастание архитектурной и микроархитектурной сложностей[^2].

Каждые 2 года компания Siemens публикует исследование, связанное с основными трендами верификации заказных цифровых схем. Последнее опубликованное (на 23.06.2024) [исследование](https://blogs.sw.siemens.com/verificationhorizons/2022/12/12/part-8-the-2022-wilson-research-group-functional-verification-study/) указывает на несколько важных фактов, а именно:

- процесс верификации цифровых устройств в среднем занимает 50-60% времени всего маршрута проектирования;
- количество инженеров-верификаторов примерно равно количеству инженеров-проектировщиков[^3];
- 49% времени инженер проектировщик проводит за верификацией.

Мало того, что процесс верификации занимает больше 50% времени в большинстве компаний, так еще и сам инженер-проектировщик тратит почти половину своего времени на отладку созданного решения.

![](../doc/pic/verif.png)

Инженеры со всего мира работают над решением задачи ускорения процессов тестирования (далее, если не указано иного, термин "тестирование" является синонимом термина "верификация"). Разрабатываются [методологии верификации](https://www.accellera.org/downloads/standards/uvm), создаются [различные системы автоматизации](https://github.com/olofk/fusesoc), предпринимаются [попытки выхода на более высокий уровень абстракции](https://www.cocotb.org).


## Верификация процессорных ядер

Системы на Кристалле состоят из множества аналоговых и цифровых устройств, работающих независимо или совместно. **Основным цифровым устройством систем в большинстве случаев является процессор**, выполняющий программную обработку цифровых данных. Сфера верификации процессорных ядер является одной из самых актуальных составляющих индустрии проектирования и тестирования сложно-функциональных блоков.

Большое количество компаний при проектировании выбирают путь использования покупных блоков, которые уже были протестированы и предоставляют определенный уровень надежности. Это касается и процессорных ядер. Например, по состоянию на 2022 год в 90% современных мобильных устройств в настоящее время установлены ядра компании ARM. Однако, **не так давно на рынке процессоров появилась многообещающая архитектура, способная к заданию новых тенденций.**


## Архитектура набора команд RISC-V

<p align="center">
  <img src="../doc/pic/riscv.svg" width=650></img>
</p>

В настоящее время все большую популярность набирает **архитектура набора команд (АНК) [RISC-V](https://riscv.org)**. В 2015 году был создан международный фонд архитектуры. Уже с 2018 года он работает в партнёрстве с [The Linux Foundation](https://www.linuxfoundation.org/).

У архитектуры есть несколько особенностей, которые делают ее крайне многообещающей как для использования во всем мире, так и в России в частности. Поговорим ниже об этих особенностях, а также о предполагаемом векторе развития АНК.


## Особенности RISC-V

### Открытость

**Основная отличительная черта архитектуры RISC-V – ее открытость.** АНК может быть использована бесплатно и без каких либо ограничений для создания как процессоров с открытым исходным кодом, так и для проектирования коммерческих решений.

Цитата с официального сайта АНК [riscv.org](https://riscv.org/about/faq):

> The RISC-V ISA is free and open with a permissive license for use by anyone in all types of implementations. Designers are free to develop proprietary or open source implementations for commercial or other exploitations as they see fit. RISC-V International encourages all implementations that are compliant to the specifications.

Стоит заметить, что решения на основе RISC-V могут успешно коммерциализированы. Ценность будет представлять собой то, каким образом реализована АНК в цифровой микросхеме. Говоря простым языком - как быстро реализация будет работать и сколько энергии потреблять.

Уже сейчас вокруг RISC-V сформировалось сообщество из десятков тысяч разработчиков, готовых к сотрудничеству и обмену опытом. **В 2022 году в России был создан [Альянс RISC-V](https://riscv-alliance.ru/)** - объединение независимых разработчиков вычислительной техники и программного обеспечения на основе данной архитектуры набора команд.

### Модульность

**Еще одной особенностью RISC-V является модульность**. Базовый набор (`I`) содержит несколько десятков инструкций, при этом в спецификациях присутствует **несколько десятков расширений** для аппаратной поддержки дополнительного функционала. Автор рекомендует отличный [ознакомительный ресурс](https://research.redhat.com/blog/article/risc-v-extensions-whats-available-and-how-to-find-it/), описывающий функционал существующих RISC-V расширений.

В дополнительные расширения входят поддержка аппартного умножения/деления (`M`), вычислений с плавающей точкой (`F`, `D`), векторных операций (`V`) и многие другие. Даже [криптографию](https://github.com/riscv/riscv-crypto/releases) "завезли". Также инженерам предоставлена возможность создания [нестандартных команд и их интеграции в архитектуру](https://www.youtube.com/watch?v=PkKfcW72NcI).

В качестве примера на изображениях ниже представлены кодировка инструкции R-типа базового набора инструкций `I` (в двоичном формате), кодировка инструкций доступа к памяти расширения `F` для вычислений с плавающей точкой. И наконец инструкций расширения `Zalrsc`, которое является подмножеством расширения `A` атомарных операций.

<p align="center">
  <img src="../doc/pic/riscv_instr.png" width=700></img>
</p>

Модульность не просто так является именно особенностью, а не очевидным плюсом АНК. Ярким примером является расширение сжатых инструкций (`C`). Оно позволяет кодировать часть 32-битных инструкций при помощи 16 бит, что приводит к потенциальному уменьшению размера программы в памяти. Однако, если рассмотреть кодировку данных инструкций, то можно убедиться, что они занимают 1/4 кодового пространства АНК. Ко всему прочему, процесс выборки и декодирования инструкций усложняется из-за того, что их размер отличается.

Тем не менее, требованием к ядру, которое запускает так называемые полнофункциональные операционные системы (rich-OS)[^4], является [соответствие профилям `RVA22U` и `RVA22S`](https://github.com/riscv/riscv-platform-specs/blob/main/riscv-platform-spec.adoc#211-general)[^5], которые включают в себя требования к аппартной поддержке `C` расширения сжатых инструкций. Простыми словами: хотите запустить Linux на своем процессоре - поддерживайте `C`. Не так давно компания Qualcomm выступила с предложением об исключении этого расширения из списка обязательных для `RVA22U` и `RVA22S` (информация доступна по [ссылке](https://lists.riscv.org/g/tech-profiles/topic/qualcomm_slides_on_c/101741936) и [ссылке](https://lists.riscv.org/g/tech-profiles/topic/101784675#322)).


## Вектор развития RISC-V

Стоит заметить, что, так как АНК является относительно "молодой", то **наблюдается малое количество высокопроизводительных решений, а также общее сравнительно небольшое количество ядер на рынке.** 

Хотя тенденция развития у архитектуры многообещающая. Например, в [опубликованное в 2022 году исследование](https://riscv.org/blog/2022/02/semico-researchs-new-report-predicts-there-will-be-25-billion-risc-v-based-ai-socs-by-2027) предсказывает к 2027 году наличие 27 миллиардов RISC-V СнК для искусственного интеллекта по всему миру.

В 2022 году [поступил в продажу первый ноутбук с ядром на архитектуре RISC-V](https://habr.com/en/companies/selectel/articles/691252/). Эта история получила продолжение: в июне 2024 года открылся предзаказ на [вторую версию](https://www.cnews.ru/news/top/2024-06-14_sozdan_supermoshchnyj_noutbuk). Множество компаний высказываются в поддержку и проводят инвестиционные программы, например:
- [RISC-V дизайн-центр в Барселоне от Intel](https://www.eenewseurope.com/en/400m-risc-v-design-centre-for-barcelona);
- [Qualcomm разработает решение на RISC-V для умных часов от Google](https://riscv.org/news/2023/10/qualcomm-to-bring-risc-v-based-wearable-platform-to-wear-os-by-google/);
- [Крупнейшая российская компания в сфере систем хранения данных Yadro "переключилась" на архитектуру RISC-V](https://3dnews.ru/1088875/yadro-ushlo-ot-ibm-i-prishlo-k-risc-v).

Представленные выше факты способствуют **созданию ядер на архитектуре RISC-V, в том числе с открытым исходным кодом**. Сообщество активно делится опытом и исследует различные подходы к оптимизации для увеличения производительности, уменьшения площади и энергопотребления кристаллов ядер.


## To be continued...

Если компания выбирает RISC-V как архитектуру для процессорного ядра своей СнК, то, **ввиду отсутствия необходимых решений на рынке готовых СФ-блоков, может появиться необходимость в разработке собственного процессора**. Однако любое новое решение необходимо верифицировать. И здесь инженеры могут столкнуться с рядом проблем, свойственных как процессорным ядрам в целом, так и конкретной архитектуре.

О том, что же такое функциональная верификация, в частности RISC-V ядер, будет рассказано в [следующем занятии](./01_basics.md).

[^1]: В общем случае, верификация цифрового устройства – процесс обоснованного доказательства его корректной работы в рамках представленной на него спецификации. Спецификация – набор задокументированных требований. Она определяет характеристики устройства. Более подробно данные термины будут разобраны в [Теме 01: Функциональная верификация процессорных ядер](./01_basics.md#верификация-цифровых-устройств).
 
[^2]: Термины архитектура и микроархитектура применительно к процессорным ядрам будут рассмотрены в [Теме 01: Функциональная верификация процессорных ядер](./01_basics.md#архитектура-и-микроархитектура-процессорного-ядра).

[^3]: Термин "инженер-проектировщик" или "проектировщик" в данном контексте аналогичен английскому термину "Design Engineer".

[^4]: Linux, FreeBSD, Windows, а также их производные.

[^5]: Для более глубокого погружения в контекст автор рекомендует ознакомиться с профилями RISC-V ([официальный репозиторий](https://github.com/riscv/riscv-profiles), [полезный ресурс](https://fprox.substack.com/p/risc-v-profiles)).
